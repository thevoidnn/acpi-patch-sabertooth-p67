# acpi-patch-sabertooth-p67
Patch for ACPI DSDT (SSDT1) table for ASUS Sabertooth P67 motherboard to get rid of errors at boot
```
kernel: ACPI BIOS Error (bug): Could not resolve [\_SB.PCI0.SAT0.SPT0._GTF.DSSP], AE_NOT_FOUND (20181003/psargs-330)
kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT0._GTF, AE_NOT_FOUND (20181003/psparse-516)
kernel: ACPI BIOS Error (bug): Could not resolve [\_SB.PCI0.SAT0.SPT2._GTF.DSSP], AE_NOT_FOUND (20181003/psargs-330)
kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT2._GTF, AE_NOT_FOUND (20181003/psparse-516)
kernel: ACPI BIOS Error (bug): Could not resolve [\_SB.PCI0.SAT0.SPT1._GTF.DSSP], AE_NOT_FOUND (20181003/psargs-330)
kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT1._GTF, AE_NOT_FOUND (20181003/psparse-516)
kernel: ACPI BIOS Error (bug): Could not resolve [\_SB.PCI0.SAT0.SPT2._GTF.DSSP], AE_NOT_FOUND (20181003/psargs-330)
kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT2._GTF, AE_NOT_FOUND (20181003/psparse-516)
kernel: ACPI BIOS Error (bug): Could not resolve [\_SB.PCI0.SAT0.SPT0._GTF.DSSP], AE_NOT_FOUND (20181003/psargs-330)
kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT0._GTF, AE_NOT_FOUND (20181003/psparse-516)
kernel: ACPI BIOS Error (bug): Could not resolve [\_SB.PCI0.SAT0.SPT1._GTF.DSSP], AE_NOT_FOUND (20181003/psargs-330)
kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT1._GTF, AE_NOT_FOUND (20181003/psparse-516)
```

Patches `DSSP` and `FHPP` as Constants instead of External Objects (which is not found in any other table).

Sets `DSSP` to `One` and `FHPP` to `Zero` by default.

Tested only on Arch Linux with GRUB.
Requires `sudo`, `iasl`, `cpio`, `sed`, `tee`, `tr` and `bc`.

If you know what `DSSP` and `FHPP` actually stands for (e.g. which `SATA` features it controls) - please let me know, because i decided to enable it (by setting it to `One`) while looking at other SSDT1 tables with `DSSP` and `FHPP` variables on github.

```
$ ./mkpatch
$ ./mkoverride
```
