---
title: "[SOLVED] Performance on USB Install"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by xphlo on 2008-10-31
I used 8.04 i386 alternate cd and did a command line install to an 8GB usb. From grub on the MBR, I use ´configfile (hd0,4) /boot/grub/menu.lst' to boot this particular installation (which also uses grub). I have installed xorg, openbox, and firefox3.0, and a few various packages.

I write because I am getting some annoying lag. Startup is always a little slow, but most programs are very quick after their first call. 
But certain programs (notably firefox) never improve.

If I stay in the same window,tab,and webpage for a while, I will get good performance with flash apps, javascript, and standard html. But anytime a new page is loaded in any way, firefox just freezes up. I cant change focus to a text field (cant type either), links wont work, scrolling, screen doesn´t repaint; the same ol. It will progressively get better over 20-30 seconds, but each new page and it starts over.

I also notice many disk WRITES while a lot of this is happening. This may be ill founded, but the disk writes and bad performance seem to go hand in hand.

I understand a usb isn´t lightning fast, but after a while, firefox should be in ram. Why am I waiting for disk writes? 

Is my root filesystem poorly configured? Do I need to add filesystems (cache,tmp,???)? 

Ill open several firefox instances, and when they start to slow down, ill post some details below.

```

xphlo:. free
             total       used       free     shared    buffers     cached
Mem:       2074220     394484    1679736          0      22960     222936
-/+ buffers/cache:     148588    1925632
Swap:            0          0          0

```

```

xphlo:. uptime
 11:13:53 up  1:21,  4 users,  load average: 1.74, 0.77, 0.61

```

```

xphlo:. mount
/dev/sdb5 on / type reiserfs (rw,relatime,notail)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/sdb2 on /home type reiserfs (rw,relatime)
/dev/sdb1 on /mnt/boot type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)

```

Thanks for any help.

---

### Post by null_pointer_us on 2008-10-31
You are talking about installing **to** a USB **flash** drive, right?

1. If it's USB, you could make sure the drive is USB 2.0 capable and plugged into a USB 2.0-compatible port.

2. Flash drives have good read performance in general, and random reads are very, very fast due to the low seek times. However, random writes to flash drives are also much, much slower than a hard drive.

3. Performance varies greatly among flash drives, depending on the chips, the controller, etc.

I wonder if Firefox is trying to keep a disk cache on the flash drive. You might try changing the size of the "temporary internet files" cache, relocate the "temporary internet files" cache to a hard drive, or perhaps disable the "temporary internet files" cache feature itself. I'm not sure exactly how to do that.

---

