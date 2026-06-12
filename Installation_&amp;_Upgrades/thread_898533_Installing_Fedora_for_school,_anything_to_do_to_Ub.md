---
title: "Installing Fedora for school, anything to do to Ubuntu first?"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by Mecharuva on 2008-08-23
I'm getting a degree in Linux System Administration and High Performance computing, and my "Introduction to Linux Systems" class comes with the Fedora 9 and Red Hat Enterprise Linux Bible.
So I was gonna put Fedora 9 on this computer here, and I have X/Kubuntu 8.04 on here already.
Should I just run the install DVD and overwrite the partition with Ubuntu on it?

---

### Post by sandysandy on 2008-08-23
just dual boot fedora and ubuntu.

fedora may or may not detect ubuntu install while writing to mbr, but that can be overcome later.

ubuntu is derivative of debian school, whereas as fedora (free version of Red Hat) uses rpm.

regards

---

### Post by Mecharuva on 2008-08-23
I was thinking of that, but..
Can I install it on the second hard drive?
My primary has no space any more...
My secondary has like 100Gb open though.

---

### Post by sandysandy on 2008-08-23
definitely, u can install it on second hard drive.

which all OS are u going to use - just fedora and ubuntu or windows also.

regards

---

### Post by Mecharuva on 2008-08-23
I currently have it dual booting Ubuntu 8.04 and Windows XP Pro SP3 from GRUB, both on the primary hard drive.

---

### Post by sandysandy on 2008-08-23
> **Mecharuva said:**
> I currently have it dual booting Ubuntu 8.04 and Windows XP Pro SP3 from GRUB, both on the primary hard drive.

that means ur comfortable with dual booting.:)

still, i am attaching some links on dual booting which u can have a look

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://apcmag.com/how_to_dual_boot_w...lled_first.htm](http://apcmag.com/how_to_dual_boot_w...lled_first.htm)

[http://apcmag.com/how_to_dual_boot_l...lled_first.htm](http://apcmag.com/how_to_dual_boot_l...lled_first.htm)

[http://www.howtoforge.com/dual_boot_..._ubuntu_feisty](http://www.howtoforge.com/dual_boot_..._ubuntu_feisty)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)

[http://lifehacker.com/software/ubunt...ntu-193474.php](http://lifehacker.com/software/ubunt...ntu-193474.php)

when installing fedora, on second hard disk, it will ask u if u want to install MBR on first hdd or second hdd or...

regards

---

### Post by Mecharuva on 2008-08-23
Alright, I'm quite angry now.
After one install, some kind of GUI epic failure, and another fresh install of Fedora,
I have it working.
Sort of.
However the new GRUB will only pick a hard drive to boot from, not letting me pick which operating system to boot.
So I've got Ubuntu & Windows on HDD1, and it will only boot to Windows.
I have no idea how to fix it.

---

### Post by Sef on 2008-08-23
Read [Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems") from the Illustrated Dual Boot.

---

### Post by Mecharuva on 2008-08-23
Okay, so I should set up a chainloader?
Now I just have to figure out how to do that from Fedora here.
Agh.

---

