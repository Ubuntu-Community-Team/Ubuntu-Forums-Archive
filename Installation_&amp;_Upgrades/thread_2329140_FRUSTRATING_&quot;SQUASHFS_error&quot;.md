---
title: "FRUSTRATING: &quot;SQUASHFS error&quot;"
date: 2016-06-28
forum: Installation &amp; Upgrades
---

### Post by S.User on 2016-06-28
Hello,

I've been trying and repeating and re-installing, changing the USB, the HDD and the installation keeps failing.

System:
It's Lubuntu 16.04 but also occures with 14.04 and DSL 4.11. I sucessfully tested Openmediavault on the same HDD.
Main board is an ASUS P5KPL.

The problem:
It starts ok from a bootable USB. Runs through the whole process until it gets to restart the system.
On restart it either gets stuck at a black screen or I'm getting a "SQUASHFS error:..." message (several lines) similar to this here:
[https://help.ubuntu.com/community/SquashfsErrors](https://help.ubuntu.com/community/SquashfsErrors)

BUT: The suggested solution is always to add to the boot kernel the lines
"ide=nodma acpi=off" (above and here [http://askubuntu.com/questions/528036/ubuntu-installation-over-usb-and-dvd-fails](http://askubuntu.com/questions/528036/ubuntu-installation-over-usb-and-dvd-fails))

Very well but I CANNOT get to the boot options at all. HOW shall I add something? Don't even get a terminal.
On boot from HDD all I'm getting is "/dev/sda2: clean 123549/1222992 files, 786209/4882432 blocks"... and a black screen.

This is ridiculous and really puts me off. Costs me so much time and I have never encountered such problems when installing Ubuntu or any other Linux variant. It has cost me three evenings and an afternoon now.
And I wonder when the system will actually be running at all.

Any ideas anyone?

Stephan

---

### Post by &amp;KyT$0P# on 2016-06-28
I think in order to add those boot options, if you don't see GRUB you have to hit Shift key after the EFI/BIOS is done loading (or if the EFI/BIOS doesn't care if you hold down Shift, hold it down until you see GRUB).  Then when you get the GRUB menu, use the 'e' key as instructed.  Look for the line that starts with "linux" and add those boot options on the end.

---

### Post by S.User on 2016-06-30
> **halogen2 said:**
> I think in order to add those boot options, if you don't see GRUB you have to hit Shift key after the EFI/BIOS is done loading (or if the EFI/BIOS doesn't care if you hold down Shift, hold it down until you see GRUB).  Then when you get the GRUB menu, use the 'e' key as instructed.  Look for the line that starts with "linux" and add those boot options on the end.

Thanks.
It's working now even though there are new problems (eth0 is not found). But that's for a different thread...

Stephan

---

