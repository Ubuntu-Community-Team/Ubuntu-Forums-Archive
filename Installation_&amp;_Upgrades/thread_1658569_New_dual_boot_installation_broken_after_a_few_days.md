---
title: "New dual boot installation broken after a few days"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by roy baatty on 2011-01-02
Hi all, 

I'm new to these forums, and just as new to Linux.  I decided to install a dual boot on my Sony Vaio recently.  Installation has not gone well.  

I attempted to install latest version desktop 10.10 with a CD.  I was able to choose a language, then screen went black.  I heard some music after a few minutes but no video.  I was eventually able to boot the system several times under recovery mode.  Several other forums and posts suggest that the problem was with my Vaio graphics card (NVIDIA GeForce GT 230M).

Now something else seems to have happened.  After the initial dual boot screen, where I'm able to choose operating system, if I choose either Ubuntu or Ubuntu safe mode a bunch of text scrolls by and ends with 

___________________________________________________________
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory 
Target filesystem doesn't ave requrested /sbin/init.
No init found.  Try passing init= bootarg.


Busybox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash) 
Enter 'ehlp' for a list of built-in commands.

(initramfs)    
___________________________________________________________

No black/blank screen, but it doesn't do anything after this.  My laptop is a Sony Vaio VPCCW14FX, specs here:

[http://www.retrevo.com/search?q=Sony+VPC-CW14FX&rt=sp&modelid=23572477](http://www.retrevo.com/search?q=Sony+VPC-CW14FX&rt=sp&modelid=23572477)

---

### Post by drs305 on 2011-01-02
Welcome to the Ubuntu forums.

To get it to boot, try this from the Grub menu:
Press "e" to edit the highlighted menuentry.
Cursor to the start of the "search" line, hold down the DEL key and remove the entire line.
On the 'linux' line, cursor to "root=UUID=somelongnumber" and change it to "root=/dev/sdXY" with XY being your drive and partition. If this is a dual install with Windows, it is probably sda5. We can troubleshoot this setting later if it doesn't boot.
At the end of the same line, remove "quiet splash" and replace with "nomodeset".

Now press CTRL-x and see if it boots.

If so, when you get to the Ubuntu desktop go to System, Administration, Additional Drivers and install your video driver. It will ask for your Ubuntu username password.

If none of this makes sense, boot a LiveCD and from the Desktop, go to the following link, run the boot info script and post the contents of the RESULTS.txt:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

