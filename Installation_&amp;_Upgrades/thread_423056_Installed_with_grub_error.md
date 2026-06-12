---
title: "Installed with grub error"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by elyod_72 on 2007-04-25
I have just installed Ubuntu on a laptop that previously had a broken verson of Fedora Core. I think grub was broken as well. I got the machine as a hand-me-down. 
So I installed U. and restarted. When it comes up, it give me a grub error 21 and won't let me go any further. I can boot off of the CD, but not the drive. Any suggestions?

---

### Post by mikewhatever on 2007-04-25
Can you open the terminal, type the commands and post the output
> sudo fdisk -l
sudo cat /boot/grub/menu.lst

---

### Post by elyod_72 on 2007-04-25
sudo fdisk -l

Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/tracks, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

     Deviced Boot          Start          End          Blocks          Id          System
/dev/hda1       *                 1          978          7855753+   83          Linux
/dev/hda2                      979        1027            393592+     5          Extended
/dev/hda5                      979        1027            393561      82          Linux swap / Solaris


sudo cat /boot/grub/menu.lst

cat: /boot/grub/menu.lst:  No such file or directory

---

### Post by bulldog on 2007-04-25
> **elyod_72 said:**
> sudo fdisk -l

Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/tracks, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

     Deviced Boot          Start          End          Blocks          Id          System
/dev/hda1       *                 1          978          7855753+   83          Linux
/dev/hda2                      979        1027            393592+     5          Extended
/dev/hda5                      979        1027            393561      82          Linux swap / Solaris


sudo cat /boot/grub/menu.lst

cat: /boot/grub/menu.lst:  No such file or directory

If you use the live cd ,you have to mount your ubuntu first.
```
sudo mkdir /mnt/rescue
sudo mount /dev/hda1 /mnt/rescue
cat /mnt/rescue/boot/grub/menu.lst
```

---

### Post by elyod_72 on 2007-04-25
cat /mnt/rescue/boot/grub/menu.lst

default     0
timeout     3
hiddenmenu


title     Ubuntu, Kernel 2.6.20-15-generic
root     (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=be09d97f-26b6-40ab-bbd7-25819704b18 ro quiet splash
initrd     /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title     Ubuntu, jernel 2.6.20-15-generic (recovery mode)
root     (hd0,0)
kernel     /boot/vmlinuz-2.6.20-15-generic root=UUID=be09d97f-26b6-40ab-bbd7-258197104b18 ro single
intitrd     /boot/initrd.img-2.6.20-15-generic

title     Ubuntu, memtest86+
root     (hd0,0)
kernel     /boot/memtest86+.bin
quiet

---

### Post by elyod_72 on 2007-04-25
Is it possible to remove the grub directory out of the /boot/ directory? Or will that seriously screw things up?

---

### Post by mikewhatever on 2007-04-25
> **elyod_72 said:**
> Is it possible to remove the grub directory out of the /boot/ directory? Or will that seriously screw things up?

Why would you want to do that? It is supposed to be there. The boot options in the menu look OK. Is that the whole menu or just the relevant part?
When installing Ubuntu, have you reformatted the drive?
Here is some info on the error 21. Does it ring any bells?

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

---

### Post by elyod_72 on 2007-04-25
I am reformatting the drive tonight and will re-install.  I will let you know how that goes.

---

### Post by elyod_72 on 2007-04-26
Well, I reformatted and re-installed and I get this grub error:
GRUB Loading Stage 1.5.

GRUB loading, please wait...
Error21

_

The cursor blinks below and that's it I can't do anything else.

Suggestions?

---

### Post by elyod_72 on 2007-04-26
I went to the Super Grub website and downloaded and burned a grub image install disc. I don't seem to be able to either fix or re-install grub. 
I did the following:

Clicked on English
Clicked on Gnu/Linux
Clicked on Fix Boot of Gnu/Linux
It errored out saying:
selectfile /grub stage1 /boot/grub/stage1

Error 15: File not found
Booting 'Not Lucky'
pause SGD has NOT succeeded :(
SGD has NOT succeeded :(

Then I hit the enter button and then again finally it taking me to a menu for Restore grub in hard disk.
Clicked on Automatically Install
It came up with the same info as before:
selectfile /grub stage1 /boot/grub/stage1

Error 15: File not found
Booting 'Not Lucky'
pause SGD has NOT succeeded :(
SGD has NOT succeeded :(

I hit enter a couple of times and I'm back to the Restore grub in hard disk menu.
Then I choose Manual Restore grub in hard disk
It came up with the following error:

selecthd

Error 15: File not Found
Press any key to continue......

Then it brings up a menu asking to choose a hard disk or partition.
I click on it gives the same error as before:

selecthd

Error 15: File not Found
Press any key to continue......

I am now in this nice loop that I can only get out of by restarting.

I then restart and when I come up to the menu again and choose boot Gnu/Linux
I get the following error:
selectfile /boot/grub/menu.lst /grub/menu.lst /boot/grub.grub.conf /grub/grub.conf

Error 15: file not found
Booting 'not lucky'

pause SGD has NOT done it :(
SGD has NOT done it :(


I also tried line command and could not install either. I went to the forum for grub and found that I could not post due to some kind of error, so that was no help.

Any suggestions?

---

### Post by adrian15 on 2007-04-27
This seems to be a corrupted partition (that does not mean that you have lost all your data).
Ask someone else how to use the command fsck from a live cd to fix the partition.

Once the partition is fixed, try to recover the grub boot with [Super Grub Disk ]("http://supergrub.forjamari.linex.org") ( Linux -> Fix of Linux Boot).

adrian15

---

