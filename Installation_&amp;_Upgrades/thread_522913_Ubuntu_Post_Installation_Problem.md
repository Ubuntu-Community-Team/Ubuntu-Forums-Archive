---
title: "Ubuntu Post Installation Problem"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by gofeddy on 2007-08-11
Hello,
          I have Windows Vista already installed in my PC. I installed Ubuntu Fiesty Fawn. When I load Windows from the boot loader, I get this message "Starting Up" and the system remains in this state until I restart it. Could you help me with the problem?:(

I did a manual install by creating a "/" partition and a "swap" partition. The GRUB loader got installed automatically.
But Ubuntu is working fine.

---

### Post by ruibernardo on 2007-08-11
Hi gofeddy,

take a look in your GRUB menu. Boot in Ubuntu, since it's working, and open a terminal (click "Applications", "Accessories", "Terminal"). In the terminal write this (it will ask for your password):

```
 sudo nano /boot/grub/menu.lst
```

Go until the end of the file and check if you got something like this:

```
 # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

If you have and it's different, post it here.

---

### Post by gofeddy on 2007-08-11
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

The only difference is, in place of "hdb1" it says "sda1"

---

### Post by ruibernardo on 2007-08-11
It's fine.

Check if the Windows partition has its boot flag enabled. On a terminal write this:

```
 sudo fdisk -l
```On the Windows partition there should be an asterisk.

```
 /dev/hdb1   *           1        1306    10490413+   7  HPFS ou NTFS
```

---

### Post by gofeddy on 2007-08-11
Yes, there is an asterisk on the partition.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4545    36507681    7  HPFS/NTFS
/dev/sda2            4546       19457   119780640    f  W95 Ext'd (LBA)
/dev/sda5            4546        9090    36507681    7  HPFS/NTFS
/dev/sda6            9091       11772    21543133+   7  HPFS/NTFS
/dev/sda7           13636       16185    20482843+   7  HPFS/NTFS
/dev/sda8           16186       19224    24410736   83  Linux
/dev/sda9           19225       19457     1871541   82  Linux swap / Solaris

But, I forgot to tell something. My PC also has a Windows XP OS which was installed before Vista. 
XP is installed in C: drive
Vista is installed in D: drive

And I installed Ubuntu by making free space.

---

### Post by ruibernardo on 2007-08-11
That all ok.

Can you browse the XP and the Vista partitions? This is to check if both partitions are fine. You can do this by going to the Places menu and clicking on Computer, then on the disk/partitions to mount and browse them.

---

### Post by ruibernardo on 2007-08-11
> **gofeddy said:**
> 
And I installed Ubuntu by making free space.

Didn't read that, sorry. 

How did you freed the space? Did you, at some point, move both beginning and end of the partitions? Did you defragment them before resizing them? Both situations can screw up Windows partitions.

---

### Post by gofeddy on 2007-08-11
> **epimeteo said:**
> That all ok.

Can you browse the XP and the Vista partitions? This is to check if both partitions are fine. You can do this by going to the Places menu and clicking on Computer, then on the disk/partitions to mount and browse them.


Yeah, I can browse all my Windows partitions without any problems.

---

### Post by gofeddy on 2007-08-11
> **epimeteo said:**
> 
How did you freed the space?

I selected the option of manually editing the partition. Then, I used up around 20 GB of my free space for the ext3 and swap partitions. I still have around 10 GB free space. I did'nt use them all.
Boot loader was set at hd(0)

I did'nt resize any of the blocks or partitions. Nor did I defragment them.

Do I need to use the Vista DVD to repair it or something.......?

---

### Post by ruibernardo on 2007-08-11
Yes, that's what I'd try next. It'll possibly delete GRUB, but you can install it again after.

---

### Post by gofeddy on 2007-08-12
I loaded the Vista DVD and overwrote the GRUB with the Vista Bootloader. But then I  could'nt boot into Ubuntu. 

So, I removed Vista and was able to dual boot XP with Ubuntu. 

Anyway, thanks for your help.

---

### Post by ruibernardo on 2007-08-12
gofeddy, 

Windows is the only OS that don't like anything else installed along with it, but take a look at this page about GRUB and the Windows bootloader (Winload). I think it can help you: 

[URL="https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"]https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows
[/URL]

---

