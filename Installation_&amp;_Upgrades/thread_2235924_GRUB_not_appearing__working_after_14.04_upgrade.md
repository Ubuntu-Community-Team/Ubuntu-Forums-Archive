---
title: "GRUB not appearing / working after 14.04 upgrade"
date: 2014-07-23
forum: Installation &amp; Upgrades
---

### Post by okay19 on 2014-07-23
I run a dual boot of Ubuntu and Windows 8.1 on my HP laptop. Before I upgraded from 13.10 to 14.04, everything worked properly (GRUB appeared on boot, both systems worked, etc). But after the upgrade, I was dropped into a rescue prompt due to [this bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977").

I created a temporary fix by keeping an Ubuntu Live CD in my drive. When the computer booted into the CD, i used its GRUB command line and ran the following command:
```
configfile (hd0,gpt2)/efi/ubuntu/grub.cfg
``` This opened my GRUB menu, and both systems still booted properly.

When I booted into Ubuntu to update software yesterday, I noticed GRUB was one of the updated packages, so I removed the CD and rebooted to see if the problem was fixed. Instead of seeing the menu or even the rescue prompt, the computer now boots straight into Windows without GRUB appearing at all. How can I resolve this problem?

---

### Post by oldfred on 2014-07-23
UEFI may need the configfile entry in the grub.cfg in the efi partition.

Many or most HP's have UEFI or Windows that will reset Windows to be default boot in UEFI boot order.
Can you boot ubuntu entry?
Often work arounds needed.

       It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by okay19 on 2014-07-23
I managed to fix the problem by making a backup of the Windows boot loader (bootmgfw.efi) and copying the GRUB loader into its place. I remembered that I had to do this with Boot Repair during the initial install. A Windows update likely overwrote the previous boot loader file.

Thanks for providing all the links with instructions.

---

