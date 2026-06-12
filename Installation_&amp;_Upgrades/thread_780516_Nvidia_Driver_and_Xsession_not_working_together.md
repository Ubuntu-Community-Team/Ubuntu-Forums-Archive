---
title: "Nvidia Driver and Xsession not working together"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by IdioticCreation on 2008-05-03
I recently upgraded to 8.04  Everything seems to work well except my Nvidia driver.  If I go to: System -> Admin -> Hardware Drivers and then enable the nvidia driver and restart my computer than the Xsession fails and and a terminal session is started instead.

If I reconfigure the xorg settings from the terminal and can boot back into the Gnome desktop just fine, but with the driver again disabled.
I tried EvnyNG and had the same problem.

Then I found this:
[http://ubuntuforums.org/showpost.php?p=4108080&postcount=355](http://ubuntuforums.org/showpost.php?p=4108080&postcount=355)

I'm using a 8600 GTS like the person in that post.  I tried and and couldn't get the driver to install.  Something about it not being able to compile the kernel.

What should I do?

Thanks,
David

---

### Post by bobnutfield on 2008-05-03
When you upgraded, it should have asked whether you wanted to keep your original menu.lst file.  If you kept this file, it is possible that you are booting the Gutsy kernel.  Type 

uname -a

in a terminal to see what kernel you are running.

Many have had this situation when keeping the original menu.lst.

Bob

---

### Post by IdioticCreation on 2008-05-03
Ohh yeah I did keep the old one.  Alright, I personally don't know what it means, but uname -a output this:
Linux david-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

Edit:
yeah in my menu.lst, this is the one I'm booting to:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0539a98b-a0c3-4d2a-9a53-d3bf11d5d9a8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```
So I guess I am using the old kernel.  How should I correct this?

---

### Post by bobnutfield on 2008-05-03
OK, you are using the old kernel with Hardy.  Just add an entry to your menu.lst file to boot Hardy with the new 2.6.24-16 kernel.  You can just create an entry just the like the original except with the new kernel and new initrd.img.  This will correct all your display problems.

Bob

---

### Post by IdioticCreation on 2008-05-03
Awesome!  Also, thanks for being patient with me...I'm kinda surprised I couldn't find this information on my own.

---

### Post by bobnutfield on 2008-05-03
Well, I got caught in this same trap, but I didn't think it would matter because I don't use Ubuntu's grub menu (I boot five different distros and WinXP).  But, thankfully, easily repaired.  The Nvidia drivers have to work with their assigned kernel or they will wreak havoc.

Regards

Bob

---

