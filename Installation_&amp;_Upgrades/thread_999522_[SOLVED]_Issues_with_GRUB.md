---
title: "[SOLVED] Issues with GRUB"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by Rizareth on 2008-12-01
A few weeks ago, I installed Intrepid Ibex on my laptop. It took care of the bootloader by itself, which was fine at the time, but now I'm having issues.
     I'm currently running Intrepid and Vista with no problems, but I am having issues booting Mandriva 2009. I want to figure this out now, because when I install Slackware, I'm likely to have the same issue...
     Originally, there was no entry for Mandriva in the bootloader, so I edited the menu.lst to include it. Obviously I did something wrong, but I don't know what, and I haven't found any solutions online.

This is the important part of my menu.lst:

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		9c5427f4-2328-4b6e-8a99-998ff785a4fb
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9c5427f4-2328-4b6e-8a99-998ff785a4fb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		9c5427f4-2328-4b6e-8a99-998ff785a4fb
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9c5427f4-2328-4b6e-8a99-998ff785a4fb ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9c5427f4-2328-4b6e-8a99-998ff785a4fb
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9c5427f4-2328-4b6e-8a99-998ff785a4fb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9c5427f4-2328-4b6e-8a99-998ff785a4fb
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9c5427f4-2328-4b6e-8a99-998ff785a4fb ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9c5427f4-2328-4b6e-8a99-998ff785a4fb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Media Player
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista
root		(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Vista Backup Partition
root		(hd0,4)
savedefault
makeactive
chainloader	+1


# This entry added by me for Mandriva 2009.0
# on /dev/sda9
title		Linux Mandriva 2009.0
kernel		(sd0,8)/boot/vmlinuz-2.6.27-desktop-0.rc8.2mnb
root=/dev/sda8




Selecting Mandriva with this configuration gives me an "error 23: error while parsing number"

sudo fdisk -l returns:
Unable to seek on /dev/sda

mount returns:
/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda8 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rizareth/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rizareth)

sudo cfdisk returns:
FATAL ERROR: Bad primary partition 3: Partition ends in the final partial cylinder
but that's probably a different issue.

As far as I know, my partitions are as follows:
1.  dell media manager
2.  windows vista
3.  linux swap partition
4.  / partition for ubuntu
5.  /home partition for ubuntu
6.  / partition for mandriva
7.  /home partition for mandriva
8.  empty space
9.  vista backup partition


any help would be greatly appreciated. thanks! :]

---

### Post by logos34 on 2008-12-02
> **Rizareth said:**
> 
# This entry added by me for Mandriva 2009.0
# on /dev/sda9
title        Linux Mandriva 2009.0
kernel        (sd0,8)/boot/vmlinuz-2.6.27-desktop-0.rc8.2mnb
root=/dev/sda8


need to fix that.  Try configfile entry (easiest).

If Mandriva / is sda9, then 

>  # This entry added by me for Mandriva 2009.0
# on /dev/sda9
title Linux Mandriva 2009.0
configfile (hd0,8)/boot/grub/menu.lst
If that doesn't work, try writing grub to mandriva / 

[B]sudo grub
[/B]
grub> **find /boot/grub/stage1**
(should return 2 locations--'hd0,8' is what you want)
grub> [B]root (hd0,8)
[/B]grub> **setup (hd0,8)**  (-->writes grub to first sector of sda9, not MBR)
grub> **quit**

Now try this entry in menu.lst:
> 
# This entry added by me for Mandriva 2009.0
 # on /dev/sda9
 title Linux Mandriva 2009.0
root (hd0,8)
chainloader +1[COLOR=Red]note: just to avoid any confusion, the smilies are '8'[/COLOR]

---

### Post by caljohnsmith on 2008-12-02
When you installed Mandriva, did you let it install its boot loader? I think it uses Grub. If so, then I agree with logos34, probably the best solution for your situation is to use the "configfile" notation to link directly to the Mandriva menu.lst in your Ubuntu menu.lst. But since you mentioned that Mandriva is on partition #6, you would want to use the following entry:
```
title Mandriva Grub Menu
configfile (hd0,5)/boot/grub/menu.lst
```
But when you say Mandriva is partition #6, do you mean sda6 or just your 6th physical partition? You need to know the sdaX number to use the above notation. Grub's numbering starts with 0, so sda1 is (hd0,0), sda2 is (hd0,1), sda3 is (hd0,2), etc. If you didn't install Mandriva with its boot loader, I think reinstalling it with the boot loader would probably be the easiest solution at this point; just make sure you specify to have the boot loader installed to the boot sector of sda6, or your Mandriva partition, rather than (hd0) or sda, which would be the MBR (Master Boot Record). I'm not sure of the details though with Mandriva about how to specify where the boot loader goes. Good luck and let us know how it goes. :)

EDIT: I see that when he said Mandriva was on the 6th partition, it must actually be sda9.

---

### Post by Rizareth on 2008-12-02
I just did what logos34 suggested with the configfile entry.
When I select the mandriva entry now, it goes to the mandriva bootloader, so everything works fine there now. Thank you very much! All I have to do now is iron out some really nasty sound issues in mandriva, and I can start using it -_-
Quick question: what exactly did that "configfile" thing do?

---

### Post by logos34 on 2008-12-03
> **Rizareth said:**
> what exactly did that "configfile" thing do?

it's just a grub command to look for menu.lst at the specified location.

enjoy

---

