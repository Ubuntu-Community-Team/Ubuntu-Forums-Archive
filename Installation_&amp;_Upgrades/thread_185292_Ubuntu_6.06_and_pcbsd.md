---
title: "Ubuntu 6.06 and pcbsd"
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by zapcojake on 2006-05-31
Hello, I installed PCbsd this morning which went well and works fine except, the bsd boot loader hangs up when I try to boot linux.  I reinstalled Grub with the Ubuntu CD I have and now I can get back to my linux but bsd is unavailable.  I am hoping to use both OS's on one computer, any help is greatly appreciated.  Thanks, Jake

---

### Post by onelife151 on 2006-07-10
Hi there and good morning. I have used pcbsd for a little while but after some researching on your problem I think i might have a solution for you. I'm assuming you had ubuntu installed on the computer and you wanted to try out pcbsd and went ahead and installed the pcbsd bootloader. According to you post you were having issues trying to boot to linux from that so you reinstall grub as your primary bootloder. Well I would suggest reinstalling PCBSD but [http://shots.osdir.com/slideshows/original.php?release=655&slide=9](http://shots.osdir.com/slideshows/original.php?release=655&slide=9)
on the seletion of where to put the bootloader. I inclued a link to  the screenshot of this option. Select no bootloader and when you finish the install either boot back into linux and modify grub manaully to inclue the pcbsd install or modify it while grub boots up. I am also including a link that might shed some light on dualbooting bsd and linux. 
[http://www.justlinux.com/forum/showthread.php?threadid=143973](http://www.justlinux.com/forum/showthread.php?threadid=143973)
Included in the link if you haven't seen it before, the gentleman in question used grub to boot over 100+ OS/s BSD and LINUX and windows and dos included. I hope this addtional link is of some use to you. Have a good day.
I wish I could be of more help but I thought i would give you my two cents.

---

