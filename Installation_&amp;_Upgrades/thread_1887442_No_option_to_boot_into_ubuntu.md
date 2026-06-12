---
title: "No option to boot into ubuntu"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by deepak.janar on 2011-11-27
I have a multboot of win 7 and win xp , i installed Ubuntu on a separate partition with grub on /boot. After install i got "grub>" prompt. I used boot-repair tool from Live USB , 
Now i get the grub menu , but there is only option to boot into windows none of the 
Ubuntu options are visible. 

I am new to ubuntu, really would appreciate any help.

---

### Post by bluexrider on 2011-11-27
boot into ubuntu and from the terminal run this command:

sudo update-grub 

then try it again

---

### Post by deepak.janar on 2011-11-27
i am unable to boot into ubuntu as windows seems to be default. When i tried sudo update-grub from LiveUSB , i got* error : cannot stat 'aufs' *

---

### Post by BC59 on 2011-11-27
You could try to see what is happening to your partitions

```
sudo parted /dev/sda print
```

and

```


sudo fdisk -l

```

---

### Post by BC59 on 2011-11-27
Look if you have this bug

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/703009](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/703009)

---

### Post by bluexrider on 2011-11-27
oops, sorry

thought you were able to boot into Ubuntu

going to do a boot repair 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by deepak.janar on 2011-11-27
Thanks guess i will try one of those methods now

---

### Post by deepak.janar on 2011-11-27
Seems like the same bug, i need to do more reading now.

---

### Post by BC59 on 2011-11-27
You should be concentrated to the #41 comment:

```
Wolfgang Griech (wolfgang-griech) wrote on 2011-11-21:	 #41
guys, the main reason behind this problem is this f.. Windows FlexNet licensing program which writes into an absolute sector of the first track of ur hard disk, in my case it was sector #48, other people report #32 or #10. Grub detects this FlexNet sector and then refuses to overwrite it with the grub boot loader, with the results u have seen and described above!

so this ain't no ubuntu bug, and also not really a grub bug, this is due to some program overwriting an area of the hard disk which normally is being reserved for boot loaders etc., and not for some f....licensing program..

pls see the following link: http://ubuntuforums.org/showthread.php?t=1661254

all ur problems above are easily solvable by following the chroot part of the comment #35 of this thread, and then erasing the FlexNet sector by the method proposed by the link above, with all the restrictions that are outlined there! So if u have an important program under Windows which uses this FlexNet licensing scheme, that program might not be working anymore, or the grub bootloader will be overwritten again some time in the future! 
```

I edited a little bit the text to avoid some -f- words!

---

### Post by bluexrider on 2011-11-27
That just may be the case. Another reason to flush windows....

---

### Post by deepak.janar on 2011-11-27
I tried reinstalling grub to the MBR overwriting it, still had the same problem ubuntu never showed up in the options.

So deleted the partitions i created and re installed with 2 changes

1. i used 11.10 instead of 11.04
2. instead of separate /boot partition i used / to install grub.

This time it turned up a rescue prompt. But after running boot-repair it managed to fix everything, i got all options and windows  able to boot into ubuntu and windows

---

