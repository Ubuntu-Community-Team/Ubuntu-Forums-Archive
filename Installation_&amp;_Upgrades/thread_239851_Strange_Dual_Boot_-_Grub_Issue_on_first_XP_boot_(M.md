---
title: "Strange Dual Boot - Grub Issue on first XP boot (MBR -overwrite)"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by amohanty on 2006-08-19
Hi All,

I am facing a strange problem with my dual boot machine. 
I just setup a new win xp sp2 - ubuntu-server machine with the following config:

1st HDD on SATA3 on Mobo:
/dev/sda1 250G - XFS - data 

2nd HDD on SATA1 on Mobo:
/dev/sdb1 40G - NTFS - Windows XP SP2
/dev/sdb2 200M - /boot
/dev/sdb5 40G - XFS - /

3rd GDD on SATA2 on Mobo:
/dev/sdc1 4G - swap
/dev/sdc6 76G - /home

The windows install went fine and loooong.

So my problems started during the server install. 
1. First for some bizarre reason the installer could/would not mount the windows partition. But thats ok, I can mount it later. 

2. Second the grub install pointed to the the wrong drive spec. Instead of
```
title		Ubuntu, kernel 2.6.15-26-server
root		(hd0,1)
```
in the menu.lst it put:
```
title		Ubuntu, kernel 2.6.15-26-server
root		(hd1,1)
```
Anyhow, that was fixable by just editing from the grub prompt.I was nicely able to boot into ubuntu-server and get my command prompt, where I promptly changed all the hd... refernces in menu.lst to point to the correct ones.

3. Then I tried booting into Windows, which worked great. The problem is now, I cannot boot into ubuntu at all. Grub doesnt show up, ESC key as soon as the box boots, doesnt work. It just _always_ boots into Windows XP :evil:, no matter what I do.

I can boot up with a Live CD and mount all the partitions. A reinstall of the server fixed it. I have not yet tried grub-install... from the live cd (which technically would work), but I am wondering if anybody else has seen this. 
What the hell's going on? Because if I cant figure it out, I will be doomed to a grub-install everytime I use windows](*,) 

I have attached my menu.lst file below (comments are edited out) - the only thing changed is the **hd1**s are all **hd0** now and the map directives in the windows xp section are commented out.

I can fix the menu.lst from windows using Ext2 IFS because my /boot is a separate ext3 partition.

Any help would be greatly appreciated.

Thanks.
AM

**PS:** Even if I were to comment out the windows xp section in the menu.lst, it still boots into windows. **Is it overwriting my MBR on first/subsequent boots?????**

```

default		0

timeout		10

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-server
root		(hd0,1)
kernel		/vmlinuz-2.6.15-26-server root=/dev/sdb5 ro quiet splash
initrd		/initrd.img-2.6.15-26-server
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-server (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.15-26-server root=/dev/sdb5 ro single
initrd		/initrd.img-2.6.15-26-server
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1

```

---

### Post by amohanty on 2006-08-20
So finally I figured out what's going on and wanted to post it for posterity, just in case some else ran into trouble with this.

The problem starts with the 3 drives (to recap):
SATA 80G   on SATA1 (/dev/sdb)
SATA 80G   on SATA2 (/dev/sdc)
SATA 250G  on SATA3 (/dev/sda)

Now for some reason grub-install during the installation and later always sets the /boot/grub/device.map to so

```

hd0  /dev/sda
hd1  /dev/sdb
hd2  /dev/sdc

```

which of course is wrong!!! Grub then tries to boot off the 250G drive and goes into convulsions, so you have to manually edit the /boot/grub/devices.map and set it all right and then redo a grub install. I still have not been able to figure out why it does this. A
```

grub-install --recheck...

```
also sets the same wrong maps.

```

grub-install /dev/sdb

```

```
grub-install '(hd0)'
``` 
at that stage will also work fine.

However heres where the windows stuff comes in. Now the default install setup grub in the MBR of **/dev/sda**, which was fine for the first bootup, since the bios polled all the available mbrs. But when I booted up Windows XP (apparently - I cant say for sure - but I can reproduce it quite consistently) it seeing nothing in **its** MBR seems to have written ntldr to it. Now subsequent bootups hit **/dev/sdb** first and thus do not even execute grub's loader.

The solution then was to install grub to **both** /dev/sda/ and /dev/sdb which works fine.

Hopefully this may be useful to somebody someday. 

Also if someone could shed some light on the possible windows behavior with some references (I cant seem to find any, although the behavior points to the abovementioned cause), it would be helpful.

AM

---

