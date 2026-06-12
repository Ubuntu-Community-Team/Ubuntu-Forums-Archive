---
title: "Recompile or Reinstall"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by MAFoElffen on 2011-04-07
I "was" going to do a CPU upgrade in one of my boxes... That I had inheritted from someone...  from what I thought was an AMD Athlon 1000 to an AMD Athon XPM 1800+... The BIOS was reporting and handling the mobile chip "weird" (as 800mhz and rebooting instead of shutdowns) so I reinstalled the original chip back in.  (Maybe I'll find a better upgrade chip for this one later.)

The original CPU turned out to be an AMD Athlon 1400 that had been setup wrong-- with 100mhz fbs bus speed instead of its 133mhz.  I reset the jumpers on the board... but then-

In tty text mode everything seems to run okay.  Graphics modes are another issue though.  Now none of the previously installed the GUI's come up... It starts the GDM fine, then goes to a screen with the the blank background, with no lower or upper bars in Ubuntu and blank backgrounds also in Xubuntu and Kubuntu.

Installed is-- Ubuntu Server 10.10, with tty text, ubuntu-desktop, kubuntu-desktop, xubuntu-desktop. (LAMP, SAMBA and ssh server.)

With a cpu-upgrade or change, Do I need to reinstall-recompile the installed packages?  Or start over again fresh?  My SYS now seems a little confused.  I could just go back to how the hardware was misinstalled, but I really would rather get it right.  Besides, if I do find a better CPU upgrade... I'm thinking whatever resolves this- that I'll have to do again.

---

### Post by MAFoElffen on 2011-04-07
Afetr spending about an hor on IRC... usign apt-get install --reinstall on the 3 desktops and no change... xsession-errors not showing what was going on... I then did removes on all 3 and then install/ with the same error.

Okay-- It's a test machine.  Now doing a complete fresh install on wiped disks... with Server 11.04beta1... will tell you (later) how it went.

Edit-- Reunstalled fresh with natty 11.04 w/ all same packages last night.  All good.  Today changed CPU to another upgrade chip with no problems.

---

