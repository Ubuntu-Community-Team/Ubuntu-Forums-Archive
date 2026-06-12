---
title: "Booting Vista, XP and Kubuntu"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by Crube on 2008-02-27
Hi.

I have a newish Acer desktop PC that came with a preinstalled Vista. I currently have Vista, XP and Kubuntu installed, but I can only boot to Vista and Kubuntu. Part of the issue seems to be the Acer Erecovery partition, that can be used to reset the settings to factory default. It is shown in Grub as Windows XP as default, and it boots from hd0,0. I want to keep this partition mainly becouse, well, I bought the damn Vista when I bought this computer, and as long as it's on a separate partition, I know it's safe, and there wont be a risk of losing the recovery DVD's.

Here's my menu.lst:

> title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c3553dc5-c08a-4d7b-8ae8-0726f0725d31 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c3553dc5-c08a-4d7b-8ae8-0726f0725d31 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# on /dev/sda1
title		Windows XP **This is the Erecovery partition**
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# on /dev/sda2
title		Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1

(# on /dev/sda3
title		Windows XP
root		(hd0,4)
savedefault
makeactive
chainloader	+1 **I added this myself when I tried to get it to boot** 

Here's what fdisk -l gives me

> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda              662617892   2135416  57301608   4% /
varrun                  907924       140    907784   1% /var/run
varlock                 907924         0    907924   0% /var/lock
udev                    907924       100    907824   1% /dev
devshm                  907924         0    907924   0% /dev/shm
lrm                     907924     34696    873228   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1              8185084   6491420   1693664  80% /media/sda1
/dev/sda2            118166104  15282008 102884096  13% /media/sda2
/dev/sda5             53247408   4134136  49113272   8% /media/sda5

When I boot to hd0,0, which I think is the erecovery partition - though named Windows XP, it shows the Windows XP loading screen for a couple of seconds and then it starts the recovery thing. I'm pretty much stuck here, and I just cant find a way to boot to my XP system. I've tried changing hd0,* setting, but it changes nothing. It just doesn't work.

And yes, I'm doing everything the hard way. I know I don't need to have 2 windows systems when I'm only going to use one, but I have so much extra HD space that I just want to get everything ready and working so that no matter what I have to do on any OS I can always just boot to another one. 

Now I just need help.

---

### Post by logos34 on 2008-02-27
Can you boot Vista?

---

### Post by Crube on 2008-02-27
Yes. Booting to Vista works perfectly

---

### Post by logos34 on 2008-02-27
Then you might want to check out EasyBCD...use it to add XP to Vista menu and get to it that way

---

### Post by bernied on 2008-02-27
> **Crube said:**
> Here's what fdisk -l gives me
```
Filesystem 1K-blocks Used Available Use% Mounted on
/dev/sda 662617892 2135416 57301608 4% /
varrun 907924 140 907784 1% /var/run
varlock 907924 0 907924 0% /var/lock
udev 907924 100 907824 1% /dev
devshm 907924 0 907924 0% /dev/shm
lrm 907924 34696 873228 4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1 8185084 6491420 1693664 80% /media/sda1
/dev/sda2 118166104 15282008 102884096 13% /media/sda2
/dev/sda5 53247408 4134136 49113272 8% /media/sda5
```
Are you sure that's the output from fdisk, it looks like what you get from the df command? fdisk would tell you what type each partition was.

How did you install your XP? Did you boot successfully to it when you installed it?

---

### Post by Crube on 2008-02-27
> **bernied said:**
> Are you sure that's the output from fdisk, it looks like what you get from the df command? fdisk would tell you what type each partition was.

How did you install your XP? Did you boot successfully to it when you installed it?

Yes it worked fine. I'm now trying to use EasyBCD but I havent been able to boot to Windows XP trough it yet.

---

### Post by logos34 on 2008-02-27
You might try booting the XP install cd (>'R' recovery console) and running error check:
[B]
chkdsk /r[/B]

---

### Post by Crube on 2008-02-27
I got it working with EasyBCD and now I can boot to every OS. Thanks for the help.

---

