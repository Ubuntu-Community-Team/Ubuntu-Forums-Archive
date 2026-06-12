---
title: "Grub boot problem :("
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by stonecoldking on 2008-09-01
Im trying to get Grub to boot up Vista on a extended partition.

This is how things stand....

In Gparted:
[[IMG]http://img222.imageshack.us/img222/8853/gpartedwn5.th.png[/IMG]](http://img222.imageshack.us/my.php?image=gpartedwn5.png)

My /boot/grub/menu.lst:
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=61bca0f1-b801-4235-9b01-8d0bcfeb0904 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=61bca0f1-b801-4235-9b01-8d0bcfeb0904 ro single
initrd		/boot/initrd.img-2.6.24-16-generic



title		Ubuntu 8.04, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

And with fdisk -l:
[[IMG]http://img68.imageshack.us/img68/7184/fdisklys9.th.png[/IMG]](http://img68.imageshack.us/my.php?image=fdisklys9.png)

The relevant vista partition has been highlighted, what do i have to put into menu.lst to dual boot vista and Ubuntu.

Cheers.

---

### Post by caljohnsmith on 2008-09-01
In your menu.lst try the following entry for Vista:
```
title   Windows Vista
rootnoverify (hd0,4)
chainloader +1
```
If that doesn't work, let me know if it returns any errors.

---

### Post by ubutufan on 2008-09-01
Add the following at the end of /boot/grub/menu.lst

title		Microsoft Windows Vista
root		(hd0,4)
savedefault
chainloader	+1

---

### Post by Herman on 2008-09-01
According to GParted, the boot flag is set to /dev/sda4, which is your Ubuntu partition.
You should set the boot flag on /dev/sda5, which contains Vista.
In some computers the boot flag is needed for Windows to boot.
You can place the boot flag there with GParted. GRUB can set a boot flag in a primary partition but not a logical partition.

It's unusual to boot Windows in a logical partition, normally Windows is only bootable in a primary partition. 
When you install Windows in a logical partition, it normally finds another Windows that's already there in a primary partition and it gives up it's vital boot loader files to the older version of Windows, so if anything goes wrong with the old Windows installation, you also lose your new Vista operating system too. At least that's the way it's designed, I don't know why. So, check to see if you have bootmgr and c:\Boot in the root of the operating system first before you waste too much time trying to boot your Vista in a logical partition. It won't boot without any boot loader. 
Refer to davidgarcin's post #6 in the following thread,  [Vista Dual Boot - BOOTMGR is missing]("http://ubuntuforums.org/showthread.php?t=319814")

Here is a good website to learn more about booting Vista, [Multibooters - Dual/Multi Booting With Vista]("http://www.multibooters.co.uk/") - McTavish.

I hope you will succeed in getting it to boot and I will be interested to watch your progress, I was able to get Windows XP to boot in a logical partition okay by itself in a similar experiment. Vista will be a bigger challenge I think. Good luck. 

This thread is mis-named though, this is not a GRUB problem, it's a Microsoft problem, and they do it to their users deliberately, without informing the user.
The solution is to change completely to Ubuntu and forget about proprietary software, it's just too troublesome.  :)

---

