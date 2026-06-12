---
title: "Ubuntu 7.04 install on a laptop already with Fedora and WindowsXP"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by yinglcs2 on 2007-05-19
hi,

I have fedora and WindowsXP installed on my laptop.  Then I add ubuntu 7.0.4 on top of them.
The installation successfully. But I can't not boot from Fedora 5 anymore. I can only choose from 
Windows/ubuntu.

1. How can I boot from get tri-boot to work: Fedora + Ubuntu + Window XP
2. how can i see the fedora partition? from ubuntu? In ubuntu? I can see /boot and Windows, but I can't see fedora. I would like to at least copy files from fedora.

 Thank you for any help.

---

### Post by Ub1476 on 2007-05-19
You have to edit the GRUB file, so it detects that Fedora actually is on your hd:)

```
sudo gedit /boot/grub/menu.lst
```

Guide here: [Linky]("http://www.apcstart.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

This is not really related to your problem, but at the bottom of the guide, it shows how you add winvista. I think you just have to edit the "root (hd0,0)" line to make it working.

---

### Post by yinglcs2 on 2007-05-20
Thanks. I take a look at the file:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cbe6046d-1f91-4588-9ea6-a93b439d8526 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

I assume, I need to add one for Fedora 5, I guess my boot partition for Fedora 5 is under /media/sda5:

$ ls -la /media/sda5/
total 8808
drwxr-xr-x 4 root root    1024 2007-04-29 12:40 ./
drwxr-xr-x 6 root root    4096 2007-05-19 21:50 ../
-rw-r--r-- 1 root root   63847 2006-03-14 15:19 config-2.6.15-1.2054_FC5smp
-rw-r--r-- 1 root root   75556 2007-04-10 14:44 config-2.6.20-1.2312.fc5smp
drwxr-xr-x 2 root root    1024 2007-04-29 12:40 grub/
-rw-r--r-- 1 root root 1789523 2007-04-29 12:14 initrd-2.6.15-1.2054_FC5smp.img
-rw-r--r-- 1 root root 1826851 2007-04-29 12:40 initrd-2.6.20-1.2312.fc5smp.img
drwx------ 2 root root   12288 2007-04-29 07:08 lost+found/
-rw-r--r-- 1 root root  831559 2006-03-14 15:19 System.map-2.6.15-1.2054_FC5smp
-rw-r--r-- 1 root root  936653 2007-04-10 14:44 System.map-2.6.20-1.2312.fc5smp
-rw-r--r-- 1 root root 1564844 2006-03-14 15:19 vmlinuz-2.6.15-1.2054_FC5smp
-rw-r--r-- 1 root root 1850548 2007-04-10 14:44 vmlinuz-2.6.20-1.2312.fc5smp

Can you please tell me how to modify the file you suggested?

Thank you.

---

### Post by Ub1476 on 2007-05-20
Well, Ubuntu, kernel 2.6.20-15-generic is Feisty Fawn, as I guess you know.
root (hd0,6): This is where it's located on hd.

I'm not sure where Fedora is on your machine, but I hope you know:)

Here's my GRUB menu file:

```
## ## End Default Options ##

title		Feisty Fawn
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=28658954-c835-4a3e-b70d-cdcba73f1361 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=28658954-c835-4a3e-b70d-cdcba73f1361 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Since you already are dual-booting XP and Linux I guess you got something similar at the bottom. I think you just have to add this to your file:

```
title Fedora Core 6 (your fedora version)
root (hd0,x)
chainloader +1
```

Where x is the partition number of the Fedora / partition. For example, if you install Fedora on hda2, then x would be 1.

Found a forum that discuss it: [Linky]("http://www.linuxquestions.org/questions/showthread.php?t=546101")

This should be rather simpel if you just have the details:P

---

### Post by yinglcs2 on 2007-05-20
Thanks. Can you please help me how can i find out which partition that I have installed Fedora on?

And how can i map that Fedora parition to Ubuntu so that i can copy files from Fedora to ubuntu?

Thank you

---

### Post by Ub1476 on 2007-05-20
Sorry, I don't know how you can find out where Fedora is installed, but you can guess:biggrin: As long as you don't use the hd o,x were your other OS's are installed it should do fine, I guess.. As for mapping, I don't know either. It worked automatic for me, you see:) But if I were you I would do some more searching, maybe create a thread were you just ask:

How can i find out which partition that I have installed Fedora on?

And how can i map that Fedora parition to Ubuntu so that i can copy files from Fedora to ubuntu?

Good luck
Ub

---

### Post by ivanoz on 2007-05-22
My problem is a bit different,

i have my laptop P3 with Win XP and Fedora 6, i want to install ubuntu, but i want to know is that if I'm able to install it in the same partition as Fedora and how to do that. (does the installer helps me with it??)

Cheers

Ivanoz

---

