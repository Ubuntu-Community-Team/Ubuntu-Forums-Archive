---
title: "PATA primary, SATA secondary = brick"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by ferreter on 2006-11-23
Hello all,

I'm in a bit of a pickle. I recently attained a SATA drive and hooked it up as one of my secondary drives on a computer running XP. I was going to install fedora as I use that for my server and a secondary workstation but I thought that I'd give (k)ubuntu a swing as there is much talk about it. But I've immediately run into an issue which I hope someone can assist with. 

Firstly I cannot use the graphical installer as the nvidia 6800 GS just doesn't seem to be supported. No biggie, I download and run the alternative install CD to install from text. 

Now prior to running the CD I changed the boot order of my drives so that the SATA drive would be the primary boot drive in the bios. When I get to the area where it installs grub I'm given the option to install to the mbr of hda1. And so I do as it specifically mentions that I'll have the oportunity to choose what I will be booting from. Well as the sata drive boots first that option means nothing and thusly nothing boots. When I change the bios boot order to boot from the IDE drive first it flashes a LILO prompt and a slax logo comes up. A bunch of messages fly by and eventually gives a kernel init error and freezes entirely. Now I may have installed slax a long time ago on this drive but I don't remember when. Besides, XP was booting fine previously anyway. 

So, I change the boot order back to the SATA drive being first and opt not to install to the mbr of hda1 and just install to \dev\sda1. On boot all I get is "GRUB" and nothing else. 

Help please I really do want to give ubuntu a chance here.

Thanks!

---

### Post by bulldog on 2006-11-23
When you install GRUB,you only need to know hd0 and hd1 and so on.
GRUB has no knowledge about hda1 or sda1.

Normally your IDE drive is seen as hd0 and your Sata as hd1,but if you set the Sata as first boot device it can be recognized as hd0 instead of hd1.

---

### Post by rplantz on 2006-11-24
> **bulldog said:**
> When you install GRUB,you only need to know hd0 and hd1 and so on.
GRUB has no knowledge about hda1 or sda1.

Normally your IDE drive is seen as hd0 and your Sata as hd1,but if you set the Sata as first boot device it can be recognized as hd0 instead of hd1.

I am also trying to install two distros, one on SATA, other on PATA. I've been using my SATA for Ubuntu and decided my first step would be to install another copy on my PATA. Since I'm comfortable installing Ubuntu, I thought this would be a good "proof of concept."

My bios lists the PATA on Channel 1 and the SATA on Channel 2. I can set the booting order for either one, but the Channel number remains the same.

The  relevant entries in my /boot/grub/menu.lst on the PATA are:
```

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc5 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```
and
```

title           Ubuntu, kernel 2.6.17-10-generic (on /dev/sda1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash 
initrd          /boot/initrd.img-2.6.17-10-generic
savedefault
boot

```

On the SATA they are:
```

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```
and
```

title           Ubuntu, kernel 2.6.17-10-generic (on /dev/hdc1)
root            (hd1,4)
kernel          /boot/vmlinuz-2.6.17.10-generic root=/dev/hdc5 ro quiet splash 
initrd          /boot/initrd.img-2.6.17-10-generic
savedefault
boot

```
If I set my bios to boot from the PATA first, it works. But setting it to boot from the SATA first causes grub to get confused if I try too boot the system on the PATA disk. (The SATA system works fine.) The error message is that it cannot find the file.

I realize that I can make everything work by setting the PATA as the first boot device, but I would like to know what grub is actually thinking. It should work either way.

My main point relative to this thread is that simply changing the boot order when you have both PATA and SATA disks installed does not work.

---

### Post by bulldog on 2006-11-24
Yes it works,but I use it for another reason,let me explain.

I have windows on my IDE disk and Ubuntu on my Sata.
I have GRUB in the Sata MBR and set this disk as first boot device.
Now I can start windows and ubuntu as well from the GRUB menu.
If I ever mess up GRUB [not likely] I can boot windows with it's own bootloader by changing the boot order.

That's why I advice to let the windows MBR to windows and install GRUB on the Ubuntu disk,if you have to disks ofcourse.

You have GRUB installed on each disk?
Can't see why someone should want that.
Can you explain why you did that?

---

### Post by rplantz on 2006-11-24
> **bulldog said:**
> 
You have GRUB installed on each disk?
Can't see why someone should want that.
Can you explain why you did that?

The Ubuntu installer did that for (to?) me, as far as I know.

I was wondering about that. Thank you for questioning me. I am going to try a fresh install of Ubuntu on my IDE disk and see if I can get rid of the grub there.

---

### Post by bulldog on 2006-11-24
Yes you should only have GRUB on the master boot device.

[to is an typo,should be two :D ]

To get rid of GRUB you can use the windows install disk in recovery mode and type fixmbr.

Or the system rescue disk which you can download here,

[http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page)

---

### Post by rplantz on 2006-11-25
A keen eye on the gentoo forums spotted my error. The file is named /boot/vmlinuz-2.6.17-10-generic and I somehow got /boot/vmlinuz-2.6.17.10-generic in my /boot/grub/menu.lst file. ("17.10" instead of "17-10"). Sigh.

My apologies to the original poster, who was trying to figure it out for a Windows/Linux dual boot. I thought my problem was related, but it turned out to be just my own stupid error.

---

### Post by ferreter on 2006-11-28
I eventually got things working by using (hd0) as my grub install location. This got me to a grub boot menu but then all of the grub locations were just wrong, it still had hd2 as the boot device for ubuntu's options and hd0 for the alternate boot. I just edited the boot option, loaded up then updated the menu.lst for grub. 

For what it is worth this happened to me again a bit later when I decided to reinstall and follow a different install guide for beryl  (non related issue). Perhaps it is my setup but the install certainly did not find the proper logical drive order.

---

### Post by bulldog on 2006-11-28
Unfortunately it is possible GRUB and user are thinking different about logical drive order.

In my understanding goes IDE before Sata,even if the Sata is set as boot device,the change that GRUB will install on the first IDE is significant.

But is some cases the Sata set as boot device is seen as (hd0).
Can't explain why,but have seen it some times now.

So if you have Sata and IDE mixed drives and you won't see GRUB the first time,just switch the boot device to see if it's on the other disk.
[can be use full for all multiple drives]

---

