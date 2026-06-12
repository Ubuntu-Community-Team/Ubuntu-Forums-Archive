---
title: "Dualboot with WinXP"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by Adromir on 2008-08-26
Hello Community,
last night i spent about 4 hours, trying to install Ubuntu as a second OS along with Windows.

I created two partitions for Ubuntu during the Installation after my WinXP- Partition on the same HD. Grub is installed automaticly. But when the installation is finished and i reboot, i cant make Ubuntu boot, just my normal WinXP is started :(

thanks for your help!

---

### Post by Pumalite on 2008-08-26
Boot your Live CD and post:
sudo fdisk -lu
You can try to reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Adromir on 2008-08-26
Thanks for the help.. I will try it, as soon as i feel like trying it again later today.
btw. how "dangerous" is it. Not that i destroy my current configuration

---

### Post by falcon61102 on 2008-08-26
Working with the GRUB isn't too bad.  The risk of losing all your data is pretty low and it's pretty easy to work with.

---

### Post by Adromir on 2008-08-26
Ok, thats good to know.. Your help is much appreciated!

---

### Post by caljohnsmith on 2008-08-26
Adromir, if you can boot into Windows fine from the Grub menu on startup, then probably all you need to do is modify your /boot/grub/menu.lst to get Ubuntu working. Boot a Live CD, open a terminal, and please post the output of the following commands:
```
sudo fdisk -lu
```
Find which is your Ubuntu partition in the form sdaX, where X will be a number, and sdaX will most likely be sda2 in your case. Next do:
```
sudo mount /dev/sdaX /mnt
sudo cat /mnt/boot/grub/menu.lst
```
If you post the output of everything above, I think that is all we will need to get your Ubuntu booting. :)

---

### Post by Adromir on 2008-08-26
Grub isnt even showing up at all. Perhaps its the Problem, that my primary partition is sdb1 and the logical drive is sdb2 the Partition with Ubuntu is sdb5 and the swap- partition is sdb6

---

### Post by falcon61102 on 2008-08-26
If you boot up from the a LiveCD and go to the terminal, run these:
```
sudo grub
find /boot/grub/stage1
```

What is the results of the find?

---

### Post by Adromir on 2008-08-26
I will do that a bit later, when i finished working. I will tell you my results then!

---

### Post by Adromir on 2008-08-26
Ok, now it happened, what i feared, i used

```
sudo fdisk -lu
```

which had this results:
```
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20482874    10241406    7  HPFS/NTFS
/dev/sda2        20482875   240107489   109812307+   7  HPFS/NTFS

[B]Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xec308cb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   401528609   200764273+   7  HPFS/NTFS
/dev/sdb2       401528610   488392064    43431727+   5  Extended
/dev/sdb5       401528673   484745309    41608318+  83  Linux
/dev/sdb6       484745373   488392064     1823346   82  Linux swap / Solaris[/B]

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
15 heads, 63 sectors/track, 330774 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0e34898

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   312576704   156288321    7  HPFS/NTFS

```

Then i continued with
```
sudo grub
find /boot/grub/stage1
```
which returned
```
(hd1,4)
```

Then
```
root (hd1,4)
setup (hd1)
```

Now GRUB is started on a boot, but whatever i choose (Ubuntu or XP) it doesnt start.
With windows i just get a blinking cursor and choosing Ubuntu, it says "Error 22 No such partition".

---

### Post by caljohnsmith on 2008-08-26
> **Adromir said:**
> 

Now GRUB is started on a boot, but whatever i choose (Ubuntu or XP) it doesnt start.
With windows i just get a blinking cursor and choosing Ubuntu, it says "Error 22 No such partition".
You don't need to worry, but you need to post your menu.lst still. Please do the following:
```
sudo mount /dev/sdb5 /mnt
cat /mnt/boot/grub/menu.lst
```
Do you know for sure which HDD you are booting on startup?

---

### Post by Adromir on 2008-08-26
ok, i did what you wrote, but it didnt changed anything.

This is the content of my menu.lst:
```


title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e30641b1-b827-4c09-8ab2-e840bb20768b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
#root		(hd1,4)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e30641b1-b827-4c09-8ab2-e840bb20768b #ro single
#initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows NT/2000/XP (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

PS. Oh and i am rather sure about the hd from which i boot. Its the one i marked bold in the fdisk results.

---

### Post by caljohnsmith on 2008-08-26
OK, it looks like all you need to do is modify your Ubuntu/Windows entries in menu.lst. From the Live CD, do:
```
sudo mount /dev/sdb5 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
That will pull up your menu.lst, and change the entries as follows:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		[COLOR="Blue"](hd0,4)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e30641b1-b827-4c09-8ab2-e840bb20768b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
In other words, for all the Ubuntu entries, use (hd0,4) instead of (hd1,4). And for Windows:
```
title		Microsoft Windows XP Professional
root		[COLOR="Blue"](hd0,0)[/COLOR]
savedefault
makeactive
chainloader	+1
```
Use (hd0,0) instead of (hd1,0). Save the file and reboot. Give that a try and tell me if you get any errors.

---

### Post by Pumalite on 2008-08-26
You can also do the following. When you get to Grub, choose the OS you want to boot, then hit 'e' and 'e' again; try different possibilities (hd0,0), etc. Then 'b' for Boot. You can later make the change permanent by editing menu.lst

---

### Post by Adromir on 2008-08-26
@caljohnsmith: Thanks for your help. Ubuntu is loading now, but my Windows still doesnt (same Problem).

@Pumalite: Thanks for the hint, i will try it, when Ubuntu is finished updating.

Other thing i am wondering about, why i havent any options in Firefox

---

### Post by Adromir on 2008-08-26
--- Sorry, double Post :(

---

### Post by caljohnsmith on 2008-08-26
> **Adromir said:**
> @caljohnsmith: Thanks for your help. Ubuntu is loading now, but my Windows still doesnt (same Problem).

@Pumalite: Thanks for the hint, i will try it, when Ubuntu is finished updating.

Other thing i am wondering about, why i havent any options in Firefox
You have NTFS partitions on all three of your HDDs; so you're sure the Windows you want to boot is on the Ubuntu HDD? If that is true, then your menu.lst entry for Windows should be correct; and that would mean that the fault is most likely with your Windows partition, and not Grub at this point. If you have a Windows Install CD, you could boot that, go into recovery mode, and run the command "fixboot" on your windows partition. Just don't be tempted to run "fixmbr". "fixboot" will repair the boot sector of your Windows partition, and that may be all you need.

---

### Post by Adromir on 2008-08-26
*sigh* Somehow i am on the way to retriev the title "Dumbest Ubuntu User today"
Now i got my working Ubuntu crashed. I just added some Programs (i think the ATI- Drivers caused the trouble) and now, after i log in into Ubuntu the screen just turns black, then white and i cant do anything (except moving the cursor).

Then i tried to repair it with the alternate Disk.. But now, GRUB is gone again and Windows starts just fine..

I am beginning to think that the best Place for Ubuntu on my PC is a virtual machine..

---

### Post by falcon61102 on 2008-08-26
In reference to your Ubuntu install, did you try booting up from the recovery mode and configuring the settings for you ATI card?  

As far as the disappearing GRUB goes, I think that may have something to do with how your drives are recognized at boot.  Based on the output of you your fdisk it appears that the drive you are using for you OS's is the second drive, yet your updated menu.lst has you booting up the first drive.  This may be generating some problems for you.  Since both drives have a boot flag it may be that they are not always booting up in the same order which is leading to the sporadic GRUB.  Check your BIOS on the boot order of your drives and you may be able to remove the boot flag from the first drive (sda) with gparted.

---

