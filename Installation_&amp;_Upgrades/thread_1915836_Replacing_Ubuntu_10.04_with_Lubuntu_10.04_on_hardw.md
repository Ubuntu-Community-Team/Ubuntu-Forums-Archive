---
title: "Replacing Ubuntu 10.04 with Lubuntu 10.04 on hardware from the year 2000"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by Cu Rua on 2012-01-27
Recently fried my computer by upgrading from Ubuntu 8.04 to Ubuntu 10.04, ignoring the minimal requirements. Suffice to say, my computer was built in 2000 with no hardware upgrades whatsoever and Lucid Lynx freezes it completely within a few minutes. With another computer, downloaded and burned Lubuntu 10.04 (first checking the specs, and I meet them just fine) onto a cd, from which I've been booting and booting and booting and installing just as many times. Each time I reinstall, it asks if I want Lubuntu to coexist with Ubuntu, and I tell it to format the drive and wipe out Ubuntu, which it supposedly does. When it boots into Lubuntu, I don't get a Grub menu, and I get an odd error message, along the lines of: 
Glibwarning  getpwuid_r process 256 (or 237, 225, 219, 239, it changes every time) failed due to unknown user id 
Using the Check Disk for Defects option on the live cd brings up 1 error on 1 file, and nothing else. Tried using the disk check in Lubuntu and it said my primary hard drive was just peachy. 
The most frustrating part is the time limit I have to do anything on my computer before it freezes up. I can download and install Firefox on the package manager, but when I use it, it freezes very quickly. I tried to remove Chromium completely, and it froze immediately. Had a similar problem when I was trying to get Ubuntu 10.04 to work, where I had about 5 minutes max to get anything done, then it would freeze. 
The only thing I can think of to do is replace my video card (which can't handle the max resolution both OSs insist on, no matter how many times I change it back to 800x600), or continue reinstalling and hope a few more bits stick each time (keeping in mind the parabol of the programmer who reinstalled everything on one computer 11 times and finally succeeded through sheer bloody-mindedness). Is there a way to wipe my hard drive without simultaneously installing a new OS? Should I just keep plugging away and hope I get lucky? I just want an LTS OS that works. 
Specs:
384 mb ram @ 133 mhz
32 mb nvidia video
pentium 3 @ 133 mhz 800
two 10 gb hard drives, primary for the OS, secondary for files  
can only boot through cd, hard drive, floppy, network (not usb)

---

### Post by Rodney9 on 2012-01-27
[https://help.ubuntu.com/community/Lubuntu/Documentation/CheckISO_CD](https://help.ubuntu.com/community/Lubuntu/Documentation/CheckISO_CD)

When one has downloaded an ISO file for installing or trying Ubuntu, it is recommended to test that the file is correct and safe to use. The MD5 calculation gives a checksum (called a hash value), which must equal the MD5 value of a correct ISO.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

