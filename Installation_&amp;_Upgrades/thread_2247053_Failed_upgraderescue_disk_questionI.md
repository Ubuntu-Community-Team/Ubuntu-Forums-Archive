---
title: "Failed upgrade/rescue disk questionI"
date: 2014-10-05
forum: Installation &amp; Upgrades
---

### Post by pdcooper on 2014-10-05
Upgraded to 14.04.1 and had kernel panic on using the new kernel, so I went into an old kernel 2.5.07 I think and got the thing going. Then I did an update/upgrades and now I have the same thing with the old kernel. Updating grub front scue disk has left me with an unbootable system with a 
file not found &grub rescue prompt.
where to from here 
/dev/sda is a Hd with windows on it
/dev/sdb1 &5 is the Ubuntu install
/dev/sdc is /home 

I've got a lot of  development stuff stuff in /var/www and /user/local.

Rescue disk (10.4 is the one i have) ,chroot , grub-update which gets me back to the kernel panic (unable to mount root FS on unknown hd(0,0)
-but that should be 1,0 I think.
if I just reinstall from the rescue disk will it overwrite my stuff in / ?

Any suggestions gratefully received.

---

### Post by sudodus on 2014-10-05
The first thing to do in situations like yours is to ***backup*** everything important to another disk.

Normally you can expect the installer to overwrite files. It wants to format the root partition too, you can stop that in the manual partitioning mode 'Something else', but all such operations are risky and can go wrong.

I would make a clean installation and afterwards re-install your development stuff from the backup into the new system.

---

### Post by pdcooper on 2014-10-05
Thanks - I've got other stuff as well so am prepared to try and sorry this out for a while.
i booted off the rescue disk, crooked into /dev/sdb1 , ran update-grub (or grub-update, whatever it is now), it found all the kernel 3.2... And the windows disk and seemed to be ok. Rebooting into the native system just says 
error:file not found.
grub rescue

So the boot isn't finding grub. Is it looking on /dev/sda which is my windows disk?
if so how do I tell it to look on /dev/sdb ?

---

### Post by sudodus on 2014-10-05
Try according to this link

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by pdcooper on 2014-10-05
ive got supergrub2  CD ,so  booted from that, it found my linux installation, gave me the edit grub option , i changed the UUID to /dev/sdb1 and i have a working system .

```
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a9131882-41ba-4ebe-9770-93cf73d69c89' {        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  a9131882-41ba-4ebe-9770-93cf73d69c89
        else
          search --no-floppy --fs-uuid --set=root a9131882-41ba-4ebe-9770-93cf73d69c89
        fi
        linux   /boot/vmlinuz-3.2.0-57-generic root=UUID=a9131882-41ba-4ebe-9770-93cf73d69c89 ro  i915.modeset=1
        initrd  /boot/initrd.img-3.2.0-57-generic
}

```
> mars@twelve-M266:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 Oct  5 17:10 755fe957-fd5b-444b-ac6c-b2c174f7cc2c -> ../../sdc5
lrwxrwxrwx 1 root root 10 Oct  5 17:10 9644AB6E44AB5033 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct  5 17:10 a9131882-41ba-4ebe-9770-93cf73d69c89 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Oct  5 17:10 c9e9613e-d0e5-4f96-94bf-655912e9f802 -> ../../sdc1
mars@twelve-M266:~$ 




so the numeric string is correct but it doesnt boot with it

---

### Post by sudodus on 2014-10-05
> **pdcooper said:**
> ive got supergrub2  CD ,so  booted from that, it found my linux  installation, gave me the edit grub option , i changed the UUID to  /dev/sdb1 and i have a working system .

```
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu  --class os $menuentry_id_option  'gnulinux-simple-a9131882-41ba-4ebe-9770-93cf73d69c89' {         recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1  --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1   a9131882-41ba-4ebe-9770-93cf73d69c89
        else
          search --no-floppy --fs-uuid --set=root [COLOR=#ff0000]a9131882-41ba-4ebe-9770-93cf73d69c89[/COLOR]
        fi
        linux   /boot/vmlinuz-3.2.0-57-generic root=UUID=[COLOR=#ff0000]a9131882-41ba-4ebe-9770-93cf73d69c89[/COLOR] ro  i915.modeset=1
        initrd  /boot/initrd.img-3.2.0-57-generic
}

```
> mars@twelve-M266:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 Oct  5 17:10 755fe957-fd5b-444b-ac6c-b2c174f7cc2c -> ../../sdc5
lrwxrwxrwx 1 root root 10 Oct  5 17:10 9644AB6E44AB5033 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct  5 17:10 [COLOR=#ff0000]a9131882-41ba-4ebe-9770-93cf73d69c89[/COLOR] -> ../../sdb1
lrwxrwxrwx 1 root root 10 Oct  5 17:10 c9e9613e-d0e5-4f96-94bf-655912e9f802 -> ../../sdc1
mars@twelve-M266:~$ 




so the numeric string is correct but it doesnt boot with it
[/CODE]

The strings marked [COLOR=#ff0000]**red**[/COLOR] are the same.

I'm confused:

- Have you got a working system now?
- Or doesn't it boot?

---

### Post by pdcooper on 2014-10-05
if i try to boot from the HD , i get a file not found, grub rescue prompt
If i boot from Supergrub2 liveCD it finds grub.cfg and  then tell it to use that, it gives me the standard ubuntu menu. The boot then stop with a kernel panic 

[http://goo.gl/A2YNzY](http://goo.gl/A2YNzY)
( apologies for the quality)
If i choose the ubuntu boot option and change the boot UUID to /dev/sdb1 it starts. 
On a couple of occasions this  boot sequence ( /dev/sdb1)  has had to wait for / to be available , so i wonder if the failure to boot from the HD is that the bootloader isnt waiting for the / HD to become available . This is an older  P4 machine , if its relevant .

HTH 

I have a working system if i boot from the CD and edit grub to point to  /dev/sdb1

thanks for your help

---

### Post by sudodus on 2014-10-05
Version 14.04 LTS

It could be that mounting the HDD does not get ready before it is used. It could be other things too, for example that some driver (for graphics or wifi or some other hardware) does not work properly or that you have not enough RAM for standard Ubuntu 14.04.1 LTS.

A computer with Pentium 4 is near the lower limit for the ultra light-weight flavour Lubuntu and the medium light-weight flavour Xubuntu.

-o-

Version 12.04 LTS

An old computer may work better with the previous long time support version Ubuntu 12.04 LTS (not standard Ubuntu, but a community re-spin, which promises support until April 2017: Bento, Bodhi or LXLE).

-o-

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It will make it easier to give relevant advice.

See also the following links
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]
[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by sudodus on 2014-10-05
It's getting late here, I might have time for only one more reply tonight. ***Other people reading this thread, please chip in and continue helping*** :-)

---

### Post by pdcooper on 2014-10-06
this enough information ? 

used for office stuff a bit of PHP programming and web. 
No games or video. My download speed is Max 1.75MB/s , usually 1.5 . thats the limiting factor for a lot of stuff  
Ubuntu with gnome2 desktop with no effects. 

> root@twelve-M266:~# lshw -short
H/W path           Device      Class       Description
======================================================
                               system      Desktop Computer
/0                             bus         8IG1000MK
/0/0                           memory      128KiB BIOS
/0/4                           processor   Intel(R) Pentium(R) 4 CPU 3.06GHz
/0/4/b                         memory      8KiB L1 cache
/0/4/c                         memory      512KiB L2 cache
/0/4/0.1                       processor   Logical CPU
/0/4/0.2                       processor   Logical CPU
/0/5                           processor   Pentium 4
/0/5/0.1                       processor   Logical CPU
/0/5/0.2                       processor   Logical CPU
/0/5/0                         memory      8KiB L1 cache
/0/5/1                         memory      512KiB L2 cache
/0/1c                          memory      1792MiB System Memory
/0/1c/0                        memory      512MiB DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: 
/0/1c/1                        memory      512MiB DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: 
/0/1c/2                        memory      512MiB DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: 
/0/1c/3                        memory      256MiB DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: 
/0/100                         bridge      82865G/PE/P DRAM Controller/Host-Hub Interface
/0/100/2                       display     82865G Integrated Graphics Controller
/0/100/6                       generic     82865G/PE/P Processor to I/O Memory Interface
/0/100/1d                      bus         82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
/0/100/1d.1                    bus         82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
/0/100/1d.2                    bus         82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
/0/100/1d.3                    bus         82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
/0/100/1d.7                    bus         82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
/0/100/1e                      bridge      82801 PCI Bridge
/0/100/1e/2        wlan3       network     RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
/0/100/1e/8        eth1        network     82801EB/ER (ICH5/ICH5R) integrated LAN Controller
/0/100/1f                      bridge      82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
/0/100/1f.1        scsi0       storage     82801EB/ER (ICH5/ICH5R) IDE Controller
/0/100/1f.3                    bus         82801EB/ER (ICH5/ICH5R) SMBus Controller
/0/100/1f.5                    multimedia  82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller


---

### Post by sudodus on 2014-10-07
Looking at these specifications,

```
/0/4                           processor   Intel(R) Pentium(R) 4 CPU 3.06GHz

/0/1c                          memory      1792MiB System Memory

/0/100                         bridge      82865G/PE/P DRAM Controller/Host-Hub Interface
/0/100/2                       display     82865G Integrated Graphics Controller
```

1. I suggest that you try a version of ***LXLE*** based on ***12.04 LTS 32-bi***t Ubuntu. I think it will work out of the box (without tweaking).

2. If you want something based on ***14.04.1 32-bit*** Ubuntu, I suggest that you try ***Lubuntu*** or ***Xubuntu*** and switch to ***UXA*** acceleration according to this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics)

---

