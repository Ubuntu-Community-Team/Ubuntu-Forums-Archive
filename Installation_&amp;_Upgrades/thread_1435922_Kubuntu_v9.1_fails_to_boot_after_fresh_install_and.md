---
title: "Kubuntu v9.1 fails to boot after fresh install and display anomalies at the desktop"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by jqpdev on 2010-03-22
Hello all... 

I'm picking up Linux again after several years.  The last version a  Linux I had was Mandrake v9.1.  However, in looking to get the  latest/greatest Linux I downloaded Ubuntu and Kubuntu.  After installing  Kubuntu the system reboots and fails to boot into the OS.  After the  P.O.S.T all I get a the word "GRUB".  There is no response to any keys  with the exception of Ctrl-Alt-Del.  I am temporarily able to get passed  the boot problem if I boot from the CD and choose boot from primary  hard menu option.  I'm not sure how to fix the boot up problem and could  use some advice.  However, using the CD to boot up the hard drives  installation leads me to my next problem.

While in a desktop session I am unable to drag windows by their title  bar.  When attempting to drag a window, the desktop becomes covered with  parts of the original window spreading all over the screen in multiple  directions.  It looks like a kaleidoscope or bad acid trip image.  I  suspect the video anomalies might be configuration related or improper  driver.  Again guidance would be greatly appreciated here.

I have a good 'ole Matrox MGA Millenium card installed into a P4 1.8ghz  system, with 512 MB ram.  The hard drive originally had an old install  of Mandrake v9.1, but all of the partitions were wiped and I created 3  new partitions:
- /dev/sda1  20GB Bootable/Primary Partition  EXT4  (Unbuntu mounted at  /)
- /dev/sda2  18GB Primary  EXT4  (Kubuntu mounted at  /mnt/Ubuntu_dsktop_91)
- /dev/sda3  2GB Swap space

My intent was to install Ubuntu on the 2nd primary partition and be able  to switch between them.  However, I tried installed Ubuntu on the first  partition (reformatted of course) and I encounter the same boot problem  and display problem.

---

### Post by jqpdev on 2010-03-22
Since my last post I installed Microsoft Windows 2000 server and Windows  XP and both installed without any hardware problems.  For each of the  installs I removed all existing partitions and created new partitions of  different lengths (Win2000 server = 14.5GB, WinXP 22.8GB).  The above  was performed to rule out any possibility of hardware errors.

Before I attempted my first Ubuntu install the hard drive had an old  working Mandrake v9.1 install, which was performed years ago on  different equipment.  Mandrake recognized the equipment changes and  still booted up properly.  Although I didn't check sound capabilities  within Mandrake.  I was able to login and reach the desktop.

As for the Ubuntu and K-Ubuntu installs... Each install is done in  graphics mode with mouse support.  All existing partitions are deleted  and new partitions of different sizes are created during each install.   After each install the system fails to load the Linux operating system  (warm and cold boots).  Immediately after the P.O.S.T information I'm  left with the word "GRUB" and a blinking cursor in text mode.  Graphics  mode is never entered.

Here are the specs on my hardware:
- Asus P4B rev 1.03 Motherboard
- Intel P4 1.8ghz CPU (retail package)
- 512MB RAM (2 sticks)
- Sound Blaster Live sound card (onboard AC97 audio is disabled via  bios)
- 3Com 3C905-TX 10/100 network card (PCI)
- Matrox MGA Millenium Video card (PCI VGA bios selected in bios setup)
- Asus 52x CDROM (IDE 2nd port)
- Western Digital  WD400 40GB Hard drive (IDE 1st port)
- Generic 1.44MB floppy drive
- NEC MultiSync FP955 Monitor
- onboard: 2x serial ports, 1x parallel ports, PS/2 keyboard and mouse,  2x USB ports, 2x IDE ports, and 1x floppy port.
- Generic cream colored PS/2 style Hewlett Packard keyboard with Windows  keys and a Windows menu key
- Microsoft optical blue USB wheel mouse

---

