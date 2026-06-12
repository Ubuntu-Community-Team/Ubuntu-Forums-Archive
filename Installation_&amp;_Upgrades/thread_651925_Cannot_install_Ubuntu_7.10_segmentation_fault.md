---
title: "Cannot install Ubuntu 7.10 segmentation fault"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by alstig on 2007-12-28
I have a Fujitsu Siemens Scaleo 800 3.6 GHZ (32-bit)
1) Downloaded ubuntu-7.10-desktop-i386.iso and burned it with Nero.
2) Restarts computer with CD
3) Choose first alternative, "Start or install ubuntu"
4) "Loading Linux Kernel" appear. Then there is a page with a lots of "OK". It starts with * Setting the system clock (OK)
In the middel of the page I can read: 
* Starting ACPI services... (OK)
Segmentation fault
5) Computer freezes at this image. After 10 minutes, have nothing happend. Can´t even take out CD. Then press Ctr+Alt+Delete. The CD comes out.
6) A text appear: "Please remove the disc, close the tray (if any) and press ENTER to continue
7) I take out the CD. Press ENTER, but nothing happend.
8) After turn off the main switch, computer finally turned off.

- What is segmentation fault? 
- What can I do to solve this?

---

### Post by ajgreeny on 2007-12-28
If you haven't done so check the md5sum of the iso file to ensure it's not corrupted during downloading.  If OK, check the burned CD at boot up of the live CD (there is an option to do this, I think, on the first menu screen).  If that is OK there must be a hardware incompatibility which should be possible to work round with one of the options when you boot, try hitting F6 (I think) at the menu and then typing **noapic **when you get to the boot prompt.

---

### Post by alstig on 2007-12-31
1) I choosed the 5th alternative when restarted computer with ubuntu disc: "Check CD for defects" The answer was: Check finished: no errors found Press any key to reboot your system.
2) When system rebooted with the disc, I pressed "F6" and wrote "noapic" with no result.
3) Rebooted pressed "F6":
Boot options t=casper initrd=/casper/initrd.gz quiet spash--
4) This time a wrote acpi=off, and pressed ENTER. Now Ubuntu started fine. (It is not installed yet, but I can see the desktop)
6) What happen if I install Ubuntu, will acpi=off be default? If not, I guess I will be stuck at the page with segmentation fault when trying to start Ubuntu.
7) I have no problem with Windows XP and ACPI. How can I solve my problem?

---

### Post by bbossola on 2008-02-13
Upgrade your BIOS to the latest version, it will solve your problem (well, it worked for me :D)
Point to:
[http://support.fujitsu-siemens.com/com/support/downloads.html](http://support.fujitsu-siemens.com/com/support/downloads.html)
and search for an up-to-date BIOS

---

### Post by ikkerus on 2008-04-12
Thanks a lot! It worked 4 me too. I flsashed my bios from 1.02 to 1.15. No configuration necesary.

But my root rights are now unaccessable. :(

---

### Post by dstew on 2008-04-12
To use "root rights" (administration privleges) use the **sudo** command. The root account is not enabled in Ubuntu, for reasons of system stability and security. You should not enable it. Just use sudo.

---

