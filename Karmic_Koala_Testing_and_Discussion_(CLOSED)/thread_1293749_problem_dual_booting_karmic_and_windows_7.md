---
title: "problem dual booting karmic and windows 7"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by raptor222 on 2009-10-17
Hi,
I'm trying to make Windows 7 dual boot with Karmic but for some reason it doesn't works.
I have Ubuntu installed on one Physical HDD and windows on another.
when I run "sudo-update" grub2 automatically finds the windows 7 installation but when I reboot and choose the win7 grub entry I get a black screen and nothing happens.

the win7 entry in grub.cfg is:
```
insmod ntfs
set root=(hd1,1)
search --no-floppy --fs-uuid --set 6a50d27550d24809
chainloader +1
```

---

### Post by sirgogo on 2009-10-17
Hi,

I've had the same problem with Windows 7, except I'm booting from the same hard drive (installed Ubuntu over Windows). First, I had the error of grub not being recognized, so it would boot into Windows as if I had not even installed Ubuntu. I fixed this by loading a Live CD and reinstalling grub.

Second, was the issue similar to yours. For some reason, GRUB hasn't been able to recognize the Windows boot partition. Starting with Vista, Windows has a "boot partition" that essentially serves as the boot manager. They made this separate partition so that the boot manager could be reinstalled if corrupted without modifying the Windows installation.

Ubuntu has been able to link Vista's boot partition to the Windows partition. However, it has inconsistent luck with Windows 7. To fix this, I suggest you boot with a Live CD or into your Ubuntu partition after you reinstall GRUB, and edit the GRUB pointer file.

Basically, Ubuntu linked the "Windows 7" pointer to the actual Windows file system, instead of to the Windows 7 Boot Manager.

Check out this link [http://www.planetamd64.com/index.php?showtopic=30677](http://www.planetamd64.com/index.php?showtopic=30677) to find how to edit the GRUB file. I'm pretty confident it will tell you to add linkers to the Windows partition (hd0,#). The instructions shouldn't be much different for you, basically keep trying to get the hd number and the partition # correct until you can finally boot into Windows.

I was kinda a amateur at this, so I kept trying manually because I didn't know how to probe for  it. In my situation, Ubuntu "renamed" the original hard drive (hd0) to (hd1). This may be because of the dual-boot scenario. In any case, good luck. Let us know how it goes.

---

### Post by oldfred on 2009-10-17
Lets start with these commands to get some idea.  I believe if windows is on your second drive there should be a drivemap command to switch drives like the old map command in legacy grub. We also do not edit grub.cfg but one or more files in the /etc/grub.d directory.

```
sudo fdisk -l
blkid
```

example of a file used by grub update to make grub.cfg

grub2 counts from 1 for partitions

### BEGIN /etc/grub.d/21_winxp ###
menuentry "Windows XP" {
       insmod ntfs
       set root=(hd1,1)
       search --no-floppy --fs-uuid --set EC0CEE940CEE595A
       drivemap -s (hd1) (hd0)
       chainloader +1
}

### END /etc/grub.d/21_winxp ###

---

### Post by raptor222 on 2009-10-17
Thanks sirgogo and old fred but unfortunately I already tried that, even wrote an custom script for that (I put it in the grub.d folder).
my win 7 system sits on hd1, I had to edit device.map to reflect that:
```
device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

and then I tried to change in the grub menu (by selecting the windows 7 entry and pressing the c button to edit the executed command) all possible variations: (hd1,1), (hd1,2) and even (hd1,0) I also tried changing the chainloader parameter to something different from +1.
the normal boot command that grub executes is:
```
insmod ntfs
set root=(hd1,1)
search --no-floppy --fs-uuid --set 6a50d27550d24809
chainloader +1
```

---

### Post by oldfred on 2009-10-17
If it is on a second drive you have to map the windows drive back to drive 0, The new command is drivemap, -s is switch.

drivemap -s (hd1) (hd0)

---

### Post by raptor222 on 2009-10-17
I just tried to boot win 7 with the uuid of sdb2, and got somwhere.
I got (both with hd1,1 and hd1,2):
```
BOOTMGR is missing
press Ctrl+Alt+Del to reboot

```

---

### Post by oldfred on 2009-10-17
If it was a clean install of win7 it creates a 100mb boot partition. If not it combines its boot with the boot of the existing windows with the boot flag on.

If your PC did not come with a complete Vista installation CD, you can download a Vista or Win 7 Recovery Disc at the following link:
Windows Vista Recovery Disc [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Vista will not repair XP(they create the boot sectors differently)

---

### Post by raptor222 on 2009-10-17
oldfred I have an clean install of windows 7.

I should mention that the pc is an virtual machine (I prototype the situation to see that everything works before actual installation).

---

### Post by oldfred on 2009-10-17
I have had no experience with virtual machines.

But it seems you still need to run fixboot from a windows repair to put the Bootmgr back.

---

