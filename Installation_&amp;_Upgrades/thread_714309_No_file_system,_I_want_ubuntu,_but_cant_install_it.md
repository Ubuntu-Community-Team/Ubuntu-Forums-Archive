---
title: "No file system, I want ubuntu, but cant install it"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by martin2844 on 2008-03-03
HI, im installing ubuntu, so i put my settings and everything, then I choose manual settings for disk partitioning, and when I choose the partition I wanted to use it sais that "ther is no root file system, correct this from the partitioning menu".

What should I do?

Ive already made a swap partition of 2GB, and the partition I want to use has aproximatley 80 Gb and it is NFTS. I did this partition by using a program in windows.

Many thanks

---

### Post by Pumalite on 2008-03-03
When you make the root partition you should plant a '/' in the mount point.

---

### Post by martin2844 on 2008-03-03
I mean, the mount point is the sda/hds/?
or is it the option where you can select /windows /dos?

im currently making this post in windows Xp, because i have problems when using the wirelless connecction with ubuntu, it crashes ubuntu when trying to connect.

thanks in advance

---

### Post by mikewhatever on 2008-03-03
Ubuntu can't be installed on an NTFS partitions. Let me suggest, abort the installation right now and do your home work.
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
[http://www.google.co.il/search?q=ubuntu+installation&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.il/search?q=ubuntu+installation&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by Pumalite on 2008-03-03
Take a look at this too:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by martin2844 on 2008-03-03
Thank you very much for the info, and for mike, I already did my homework! :)

Anyways gonna tryit now, im going to change NFTS for EXT3, that way it should be dual right?

thanks again for your time!

---

### Post by mikewhatever on 2008-03-03
Holding fingers crossed for you.

---

### Post by martin2844 on 2008-03-03
Mikewhatever, thank you, your fingers helped ME!!!

I have now 7.10 UBUNTU running, everithing works perfectly although i would like to know how to acces that partition from windows. THANKS FOR YOUR HELP, BOTH OF YOU. YOU SURE ARE PROS. 

thanks again

cheers from argentina

martin

---

### Post by mikewhatever on 2008-03-03
Which partition do you want to access?

---

### Post by Pumalite on 2008-03-03
Install this driver if you want to see Ubuntu from Windows:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by martin2844 on 2008-03-05
Ubuntu removed, I had problems with internet wi-fi Connection. It connected to the network but then Ubuntu Crashed. I have 7.10 Gutty 64 bit (I have Athlon AMD 64 X2), I recieved it from netherlands a few weeks ago.

Anyways, i decided to try Wubi. But problems with Grub. I start windows and I have the windows boot menu which says:
Windows Xp

Ubuntu

I choose ubuntu and after that it gives me the famous error 17. I tried to correct the Main.Lst but no luck. Im gonna try and reinstall it.

Any suggestions on why Ubuntu will crash when using Wireless network?

Thank you very much

---

