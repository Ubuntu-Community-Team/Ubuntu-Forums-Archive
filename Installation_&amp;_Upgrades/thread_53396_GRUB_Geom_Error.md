---
title: "GRUB Geom Error"
date: 2005-07-31
forum: Installation &amp; Upgrades
---

### Post by Tomlin on 2005-07-31
I'm getting a "GRUB Geom Error" when the install is attempting to finish. It ejects my CD-ROM, and says to hit continue to finish. When it comes back up, I get the error.

I've wiped the disk clean (thinking there was "residue" from an old RH 8.0 install), but still no luck. Could the MBR be messed up?

I've NEVER had this much trouble installing ANY linux distro before. This includes RH 7.0, 7.1, 7.3 and 8.0 and Suse 9.0, 9.1 and 9.2.

I'm thinking it's more trouble than it's worth. Is there any reason I should keep trying to figure this out? I was happy with Suse, but a friend says good things about Ubuntu.

 ](*,)

---

### Post by amohanty on 2005-07-31
There are several possible sources of the problem so here goes some things you can try:

1. Make sure that all drives are enabled in the BIOS
2. Make sure all drives are setup as Auto in the BIOS
3. Look for a BIOS upgrade, if there is one, try that too.
4. Make sure you are installing Ubuntu in the primary master HDD, doesnt matter if you have another OS installed on it, the installer will detect it.
5. I usually run an fdisk /mbr off of a dos boot disk, and remove all partitions to ensure clean install, if I am doing a clean install with no other OSs on the drive.

IF nothing else works you probably ran into this [http://www.gnu.org/software/grub/manual/grub.html#Stage1%20errors](http://www.gnu.org/software/grub/manual/grub.html#Stage1%20errors)

A possible solution for Suse is at:
[http://portal.suse.com/sdb/en/2003/03/fhassel_geom-error.html](http://portal.suse.com/sdb/en/2003/03/fhassel_geom-error.html)
which should work since GRUB still is the same.

AM

---

### Post by Tomlin on 2005-08-01
Well, on the last UNSUCCESFUL install attempt, I noticed some type of error mentioning "framebuffer". It flashed across the screen too fast to read. So....I rebooted to the install CD and rather than just hit <enter>, I typed in:

linux debian-installer/framebuffer=false

AND IT WORKED!!!!  It was an example listed on the help screen. I have NO idea what it is, but I'm up and running now.

Thanks

---

### Post by mingus on 2005-08-01
[QUOTE=Tomlin]
linux debian-installer/framebuffer=false

AND IT WORKED!!!!  It was an example listed on the help screen. I have NO idea what it is, but I'm up and running now.
[/QUOTE]

Framebuffer is a video abstraction layer that permits text to be displayed in "graphical" mode (132 columns, clean font) although not actually running under a graphics server (X).  The default driver is vesafb, which apparently could not properly communicate with your video device at that time.

To determine where things stand now post-install, do a Ctrl-Alt-F2 to go to a tty (Ctrl-Alt-F7 will bring you back).  If the text looks good then the install got the framebuffer config figured out and you're done.  If not, then look in /boot/grub/menu.lst for the "kernel" line - it should have an argument like "vga=771".  Or you can look for another framebuffer driver specific to your video device; this route will require additional somewhat technical steps to implement.

---

