---
title: "[SOLVED] Partition Grub Problem"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by JohnSearle on 2008-10-31
I just installed Windows XP on my HD after a Ubuntu 8.10 clean install... The problem is that the order I installed these resulted in my grub missing the XP option.

Here's the results of my fdisk -l:
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c2c8c2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12163    97699266   83  Linux
/dev/sda2           12164       12406     1951897+   5  Extended
/dev/sda3   *       12407       19456    56629125    7  HPFS/NTFS
/dev/sda5           12164       12406     1951866   82  Linux swap / Solaris

and I tried to add the following to my grub based on advice from forums and such:
> # This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsoft Windows XP
root		(hd0,2)
savedefault
makeactive
chainloader	+1title Windows XP
root (hd0,3)
makeactive
chainloader +1 

I get the following error from doing it:
> Error 1: Filename must be either an absolute pathname or blocklist.

and I've also tried:

> title Windows XP
root (hd0,3)
makeactive
chainloader +1 

for the result of some other error...

Could someone help me out with this? I've been searching for a couple hours now, and I can't seem to find the proper way to configure this.

Thanks,

- John

---

### Post by francisc1701 on 2008-10-31
See here: [http://www.sorgonet.com/linux/grubrestore/]("http://www.sorgonet.com/linux/grubrestore/")
It describes how to reinstall grub.

Strange, though, that you still have grub in the MBR, not ntldr. I thought windows overwrites the MBR with its own bootloader during installation.

---

### Post by Pumalite on 2008-10-31
It seems you installed XP inside of an extended partition. Windows likes primary partitions.
Post a screenshot of gparted.

---

### Post by francisc1701 on 2008-10-31
> **Pumalite said:**
> It seems you installed XP inside of an extended partition. Windows likes primary partitions.
Post a screenshot of gparted.
I think I read somewhere that logical partitions begin with number 5. His NTFS partition seems to be sda3, thus not a logical partition, but a primary one.

---

### Post by JohnSearle on 2008-10-31
> **Pumalite said:**
> It seems you installed XP inside of an extended partition. Windows likes primary partitions.
Post a screenshot of gparted.

OK, then.

I just attempted to add: 

> title Windows XP
        rootnoverify (hd0,3)
        chainloader +1


based on the francisc1701 link, but I ended up with the following error:

> error 13: Invalid or unsupported executable format

Thanks for the replies guys, and could some more :)

- John

---

### Post by francisc1701 on 2008-10-31
Does anyone know what that exclamation mark next to sda3 means? If I had to guess I'd say GParted detected a problem with that partition. Since grub gives you error 13 I think there's something wrong with your xp installation.

---

### Post by Pumalite on 2008-10-31
Try to fix your Windows MBR and later reinstall Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by caljohnsmith on 2008-10-31
Your Windows is on sda3, so the following should work to boot it:
```
title Windows XP
root (hd0,2)
makeactive
chainloader +1 
```
Add that to the very end of your menu.lst, and make sure there is at least one blank line before it. Reboot, and let me know exactly what happens when you try it from the Grub menu, and we can work from there if it doesn't work. :)

---

### Post by JohnSearle on 2008-10-31
Thanks guys... it's working now.

I ended up using my Windows disk to fix the MBR (recover mode->"FIXMBR"), which brought it back to a regular windows install MBR. Then I reinstalled grub using the guide that Pumalite posted. Finally, I used the grub code that caljohnsmith posted.

Thanks to all.

- John

---

### Post by haylun98 on 2008-10-31
How did you install XP? Did you have to hide sda1(/root) first? If so may be you need an extra command in grub's menu.lst to set ubuntu partition hidden from XP:
add these under XP boot item:
#hide 1st partition:
hide (0,0)
#unhide 3rd partition:
unhide (0,2)

Just to be safe add these under Ubuntu:
unhide (0,0)
hide (0,2)

I used this method to enable my triple boot setup: Vista/XP/Ubuntu happily independent of each other. I can see your partition setup is troublesome: Primary then Extended then Primary again. My simplier solution is to reinstall XP in the 1st primary partition then install Ubuntu in the middle partitions, leaving the reminder space at the end for data.

---

