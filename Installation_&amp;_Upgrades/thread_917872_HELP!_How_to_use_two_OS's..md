---
title: "HELP! How to use two OS's."
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by ds1jr on 2008-09-12
Hey I need help. I have Ubuntu on one HDD and Windows XP Home on the other HDD. It won't let me boot to Windows now. How do I change this?

---

### Post by knattlhuber on 2008-09-12
Please open a terminal window (Applications > Accessories > Terminal), run the following commands and post the output:

```
cat /boot/grub/menu.lst
sudo fdisk -l
```

---

### Post by ds1jr on 2008-09-12
ok I did exactly like you said so here is everything,it is very long! 

> cat /boot/grub/menu.lst 
# menu.lst - See: grub(8), info grub, update-grub(8) 
#            grub-install(8), grub-floppy(8), 
#            grub-md5-crypt, /usr/share/doc/grub 
#            and /usr/share/doc/grub-doc/. 
 
## default num 1 
# Set the default entry to the entry number NUM. Numbering starts from 0, and 
# the entry number 0 is the default if the command is not used. 
# 
# You can specify 'saved' instead of a number. In this case, the default entry 
# is the entry saved with the command 'savedefault'. 
# WARNING: If you are using dmraid do not use 'savedefault' or your 
# array will desync and will not let you boot your system. 
default		0 
 
## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout		3 
 
## hiddenmenu 
# Hides the menu by default (press ESC to see the menu) 
hiddenmenu 
 
# Pretty colours 
#color cyan/blue white/blue 
 
## password ['--md5'] passwd 
# If used in the first section of a menu file, disable all interactive editing 
# control (menu entry editor and command-line)  and entries protected by the 
# command 'lock' 
# e.g. password topsecret 
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/ 
# password topsecret 
 
# 
# examples 
# 
# title		Windows 95/98/NT/2000 
# root		(hd0,0) 
# makeactive 
# chainloader	+1 
# 
# title		Linux 
# root		(hd0,1) 
# kernel	/vmlinuz root=/dev/hda2 ro 
# 
 
# 
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST 
 
### BEGIN AUTOMAGIC KERNELS LIST 
## lines between the AUTOMAGIC KERNELS LIST markers will be modified 
## by the debian update-grub script except for the default options below 
 
## DO NOT UNCOMMENT THEM, Just edit them to your needs 
 
## ## Start Default Options ## 
## default kernel options 
## default kernel options for automagic boot options 
## If you want special options for specific kernels use kopt_x_y_z 
## where x.y.z is kernel version. Minor versions can be omitted. 
## e.g. kopt=root=/dev/hda1 ro 
##      kopt_2_6_8=root=/dev/hdc1 ro 
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro 
# kopt=root=UUID=a5e3a197-3b33-4055-bdd5-6103e317b8c3 ro 
 
## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 
 
## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,0) 
 
## should update-grub create alternative automagic boot options 
## e.g. alternative=true 
##      alternative=false 
# alternative=true 
 
## should update-grub lock alternative automagic boot options 
## e.g. lockalternative=true 
##      lockalternative=false 
# lockalternative=false 
 
## additional options to use with the default boot option, but not with the 
## alternatives 
## e.g. defoptions=vga=791 resume=/dev/hda5 
# defoptions=quiet splash 
 
## should update-grub lock old automagic boot options 
## e.g. lockold=false 
##      lockold=true 
# lockold=false 
 
## Xen hypervisor options to use with the default Xen boot option 
# xenhopt= 
 
## Xen Linux kernel options to use with the default Xen boot option 
# xenkopt=console=tty0 
 
## altoption boot targets option 
## multiple altoptions lines are allowed 
## e.g. altoptions=(extra menu suffix) extra boot options 
##      altoptions=(recovery) single 
# altoptions=(recovery mode) single 
 
## controls how many kernels should be put into the menu.lst 
## only counts the first occurence of a kernel, not the 
## alternative kernel options 
## e.g. howmany=all 
##      howmany=7 
# howmany=all 
 
## should update-grub create memtest86 boot option 
## e.g. memtest86=true 
##      memtest86=false 
# memtest86=true 
 
## should update-grub adjust the value of the default booted system 
## can be true or false 
# updatedefaultentry=false 
 
## should update-grub add savedefault to the default options 
## can be true or false 
# savedefault=false 
 
## ## End Default Options ## 
 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a5e3a197-3b33-4055-bdd5-6103e317b8c3 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic 
quiet 
 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a5e3a197-3b33-4055-bdd5-6103e317b8c3 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic 
 
title		Ubuntu 8.04.1, memtest86+ 
root		(hd0,0) 
kernel		/boot/memtest86+.bin 
quiet 
 
### END DEBIAN AUTOMAGIC KERNELS LIST 
salmonowicz@salmonowicz-desktop:~$ sudo fdisk -l 
 
Disk /dev/sda: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xec1fec1f 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS 
 
Disk /dev/sdb: 80.0 GB, 80000000000 bytes 
255 heads, 63 sectors/track, 9726 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x9dc96e9e 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1        9349    75095811   83  Linux 
/dev/sdb2            9350        9726     3028252+   5  Extended 
/dev/sdb5            9350        9726     3028221   82  Linux swap / Solaris 
salmonowicz@salmonowicz-desktop:~$  

---

### Post by knattlhuber on 2008-09-12
OK, one more command..

```
cat /boot/grub/device.map
```

---

### Post by ds1jr on 2008-09-12
This is what it says, 

(hd0) /dev/sda

---

### Post by knattlhuber on 2008-09-12
Ugh. That is weird. Your drive with XP on it is mapped to hd0 which is listed as the root for Ubuntu in your boot loader.
Did you physically swap the drives or something after the installation?

---

### Post by ds1jr on 2008-09-12
Ok. I originally wanted it set up so that Windows XP would be the primary OS. So I have it on the master drive (the 160 GB) That is set up as the master drive. Ubuntu is on the 80 GB (slave) drive. When I installed Ubuntu on it I installed it to the slave drive. Since then I have swapped them around trying to get it to boot to XP.

---

### Post by knattlhuber on 2008-09-12
There is only one HD listed in /boot/grub/device.map
Add the second drive by doing

```
gksudo gedit /boot/grub/device.map
```

and adding

```
(hd1)   /dev/sdb
```

in the second line. Save the file.

Also, there is no entry for Windows XP in the GRUB boot loader file. You can add the entry manually, but before you do it, be aware that if you do something wrong, it may render your machine unbootable. Therefore, do not proceed unless you have created a copy of your /boot/grub/menu.lst file by doing

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

(To restore the original file from your copy in case you end up with a terminal prompt, you would do:

```
sudo mv /boot/grub/menu.lst.bak /boot/grub/menu.lst
sudo update-grub
```

and restart.)

Having said that, if you do below changes correctly, the worst that can happen is that your machine will hang trying to boot XP. You'll still have Ubuntu to fall back on.

OK, here goes. Open the menu.lst file for editing

```
gksudo gedit /boot/grub/menu.lst
```

Under

```
title Ubuntu 8.04.1, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet
```

add

```
title Windows XP Home Edition
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1
```

Save the file. In a terminal, type

```
sudo update-grub
```

Restart your computer. Early in the boot sequence, it asks you to hit Esc to enter the boot menu. Do so and choose 'Windows XP'. Windows should now boot. If not, reboot into Ubuntu. Either way, let us know how it worked.

---

### Post by ds1jr on 2008-09-13
I did exactly what you said. Followed the coding exactly and checked to make sure. It rendered the computer completely unbootable to either OS. I guess I will just boot from the Windows disk and reinstall it. Then I will mess with Ubuntu again.

---

### Post by knattlhuber on 2008-09-13
OMG :(  I'm so sorry. Did you try to restore the original grub file?

---

### Post by caljohnsmith on 2008-09-13
Ds1jr, there's no need to reinstall Windows as I'm sure we can get your Grub working again. When you boot now, does it show you the Grub menu, and you just can't boot any OS? Or on start up do you not even get the Grub menu, and if so, what errors do you get?

---

### Post by caljohnsmith on 2008-09-13
> **knattlhuber said:**
> 
(To restore the original file from your copy in case you end up with a terminal prompt, you would do:

```
sudo mv /boot/grub/menu.lst.bak /boot/grub/menu.lst
[COLOR="Blue"]sudo update-grub[/COLOR]
```

and restart.)

Knattlhuber, I just wanted to point out that if you restore the menu.lst with the first "mv" command, and then run "sudo update-grub" the update-grub command will overwrite the menu.lst that you just restored with with a new one that the update-grub command creates. I think it is better to add the correct Windows entry to menu.lst manually, rather than take a chance and let update-grub blindly set up a new menu.lst from scratch. :)

---

### Post by knattlhuber on 2008-09-13
> **caljohnsmith said:**
> Ds1jr, there's no need to reinstall Windows as I'm sure we can get your Grub working again. When you boot now, does it show you the Grub menu, and you just can't boot any OS? Or on start up do you not even get the Grub menu, and if so, what errors do you get?

I'm totally devastated that I screwed up his boot menu. I've done these mods before and I felt confident making this suggestion to him. Can you see where I went wrong in my posting?

---

### Post by caljohnsmith on 2008-09-13
> **knattlhuber said:**
> I'm totally devastated that I screwed up his boot menu. I've done these mods before and I felt confident making this suggestion to him. Can you see where I went wrong in my posting?
It's OK, what you asked him to do is quite easily fixable. :) I think your confusion is about the update-grub command; that command creates a new menu.lst that will overwrite any existing menu.lst, so you don't want to use it after updating your menu.lst manually. So your directions were great up until the points where you had him run the update-grub commands, and unfortunately it undid everything that you had him manually do to his menu.lst. I hope he isn't reinstalling Windows though, because fixing his menu.lst would not be a big deal at this point. :)

---

### Post by ds1jr on 2008-09-13
Ok. Here's what happens. I turn the PC on and it will get to the GRUB loader. I press ESC and get to the selection. There IS one there for XP and the three other normal ones but it will not boot to any of them. It will say "Partition was not mountable"

---

### Post by caljohnsmith on 2008-09-13
OK, reboot your machine, press ESC to get your Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)", press "e" to edit it, change it to "root (hd0,0)", press return, then press "b" to boot the entry. If your menu.lst is not in too bad of shape, that should work to temporarily boot Ubuntu. If it does work, when you get into Ubuntu, do the following commands:
```
gksudo gedit /boot/grub/menu.lst &
```
Edit all the Ubuntu entries in the menu.lst to use "root (hd0,0)". Also add the following entry for Windows at the end of your menu.lst:
title Windows XP
```
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
```
Save, reboot, and see if you can boot Windows. If you were not able to boot into Ubuntu by editing your Grub's menu on start up, let me know and we'll work from there.

---

### Post by meierfra. on 2008-09-14
I don't see how knattlhuber instruction (if followed correctly) could have caused   the problem.  "update-grub"   uses the "#groot" line in menu.lst to determine the root  line for "ubuntu".   The posted "menu.lst" contains "#groot (hd0,0)". So the root lines for ubuntu still should say "root (hd0,0)". 

Anyway, if caljohnsmith  instruction don't solve your problem,  post your menu.lst again and let us know whether anything else has changed since the last time you successfully booted Ubuntu.

---

### Post by caljohnsmith on 2008-09-14
> **meierfra. said:**
> I don't see how knattlhuber instruction (if followed correctly) could have caused   the problem.  "update-grub"   uses the "#groot" line in menu.lst to determine the root  line for "ubuntu".   The posted "menu.lst" contains "#groot (hd0,0)". So the root lines for ubuntu still should say "root (hd0,0)". 

Anyway, if caljohnsmith  instruction don't solve your problem,  post your menu.lst again and let us know whether anything else has changed since the last time you successfully booted Ubuntu.
You're right, that was my own misinformation, because I see upon further investigation that update-grub will not simply overwrite the existing menu.lst. The last time I used update-grub was to simply create a menu.lst when one didn't exist, so I erroneously assumed that it would overwrite any existing menu.lst. My sincere apology for the confusion, knattlhuber, I stand corrected.

---

### Post by knattlhuber on 2008-09-14
> **caljohnsmith said:**
> You're right, that was my own misinformation, because I see upon further investigation that update-grub will not simply overwrite the existing menu.lst. The last time I used update-grub was to simply create a menu.lst when one didn't exist, so I erroneously assumed that it would overwrite any existing menu.lst. My sincere apology for the confusion, knattlhuber, I stand corrected.

No worries. I still wonder though what went wrong.

menu.lst :
```
# groot=(hd0,0)
...
title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=a5e3a... ro quiet splash 
```

fdisk -l :
```
/dev/sda1 * 1 19456 156280288+ 7 HPFS/NTFS 
```

device.map :
```
(hd0) /dev/sda
```

hd0,0 is mapped to the windows drive, while the Ubuntu boot stanza looks for the kernel in hd0. Could that be it? For some reason that worked fine for him for booting into Linux but I wonder if the update-grub messed that up somehow.
Also, it's possible that simply physically swapping his drives may have fixed the boot problem..

---

### Post by knattlhuber on 2008-09-14
ds1jr pm'd me that that was an extra laptop that he had, not his primary production machine. Pheeeeew....:)

---

### Post by caljohnsmith on 2008-09-14
> **knattlhuber said:**
> 
hd0,0 is mapped to the windows drive, while the Ubuntu boot stanza looks for the kernel in hd0. Could that be it? For some reason that worked fine for him for booting into Linux but I wonder if the update-grub messed that up somehow.
Also, it's possible that simply physically swapping his drives may have fixed the boot problem..
When you boot Grub on start up, it sees the drive order as the same as the BIOS boot order, which is not necessarily the same as the way Ubuntu orders devices in /dev. So (hd0) is not necessarily mapped to his Windows drive on start up; (hd0) is simply the drive that is first in the boot order. I know that's confusing since device.map might say otherwise, but from my experience, that's because device.map is used only when you run Grub in the CLI and use the option:
```
sudo grub --device-map=/boot/grub/device.map
```
I confirmed this by completely changing my device.map to contain bogus drives, or I could even move the device.map to another location, and yet on start up, Grub still boots all the OSes just fine. And also, when you run:
```
sudo grub
```
You'll notice it says "probing for BIOS devices", so unless you use the "--device-map" option, even "sudo grub" ignores the existing device.map.

So bottom line, if ds1jr's Ubuntu is on the HDD first in the boot order, then (hd0,0) should be correct for Ubuntu, and Windows will be on (hd1,0). If he instead has Grub installed to the MBR of his Windows HDD and is booting from that drive, then Ubuntu should be (hd1,0) and Windows (hd0,0). 

Anyway, as I explained, that is my understanding based partly on the conclusions I've drawn from removing/changing the device.map file. Meierfra has a lot more experience with Grub and multiple HDDs than I do, so I'm sure he will be kind enough to correct me again if I'm wrong. And I sincerely appreciate being corrected when I am mistaken so I don't spread any misinformation. :)

---

### Post by meierfra. on 2008-09-14
> That's because device.map is used only when you run Grub in the CLI and use the option:

sudo grub --device-map=/boot/grub/device.map

You are right that device.map is not used during booting, but there are other cases where the device.map is used, see

[http://ubuntuforums.org/showthread.php?t=442945#55]("http://ubuntuforums.org/showthread.php?t=442945#55")

For  example update-grub uses the device.map if there is no "groot" statement in menu.lst. So if the  OP deleted or renamed menu.lst, then update-grub would have generated the wrong menu.lst. 

Anyway,  the problem might be unrelated to "menu.lst" and only occurred by  coincidence.

---

### Post by ds1jr on 2008-09-16
Ok everyone, THANKS FOR ALL OF YOUR INPUT AND HELP! unfortunately even after editing everything it still will not boot to anything. SO, I have reinstalled Ubuntu to the same drive, (Wiping it clean first of course). So here is the setup, Two HDDs. 160 GB Master, 80 GB Slave. 160 GB has Windows XP on it, 80 GB has Ubuntu. Now, give me the commands to make it bootable to both. We got a clean slate :)

---

### Post by caljohnsmith on 2008-09-16
> **ds1jr said:**
> Ok everyone, THANKS FOR ALL OF YOUR INPUT AND HELP! unfortunately even after editing everything it still will not boot to anything. SO, I have reinstalled Ubuntu to the same drive, (Wiping it clean first of course). So here is the setup, Two HDDs. 160 GB Master, 80 GB Slave. 160 GB has Windows XP on it, 80 GB has Ubuntu. Now, give me the commands to make it bootable to both. We got a clean slate :)
First of all, can you set your BIOS to boot the 80 GB Ubuntu HDD first? If you can, that is most ideal. If you can't, we can still deal with it. :) But let me know first before we proceed.

---

### Post by ds1jr on 2008-09-16
Well I want it like this so that the 160 GB is the master. So it would boot from that one first but it doesn't because the GRUB loader interferes with that and auto loads the slave drive cause it has Ubuntu. I just want to be able to boot to Windows too!

---

### Post by caljohnsmith on 2008-09-16
> **ds1jr said:**
> Well I want it like this so that the 160 GB is the master. So it would boot from that one first but it doesn't because the GRUB loader interferes with that and auto loads the slave drive cause it has Ubuntu. I just want to be able to boot to Windows too!
OK, if you want to keep the 160 GB HDD first in the boot order, the easiest thing to do is install Grub to the master boot record (MBR) of that drive, and have all of Grub's system files (menu.lst, etc) on the Ubuntu slave HDD. If your master drive was first in the BIOS boot order when you installed Ubuntu, that is what should have happened by default. You said you all ready installed Ubuntu--so what happens when you start your computer now? Do you get a Grub menu?

---

### Post by ds1jr on 2008-09-16
So when I start it and go to the GRUB menu it is the same thing. Windows XP is not listed. When I installed it it wanted to install to the 160 GB HDD but I told it to do a guided install to the 80 GB slave drive. So now what? :( I don't care which it will automatically boot to as long as I can choose on bootup.

---

### Post by caljohnsmith on 2008-09-16
> **ds1jr said:**
> So when I start it and go to the GRUB menu it is the same thing. Windows XP is not listed. When I installed it it wanted to install to the 160 GB HDD but I told it to do a guided install to the 80 GB slave drive. So now what? :( I don't care which it will automatically boot to as long as I can choose on bootup.
OK, so you can't boot into Windows, but what about Ubuntu? If you can boot into Ubuntu, open a terminal, and please post:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```

---

### Post by ds1jr on 2008-09-16
Yes I can boot into Ubuntu. Here is the code. Be warned, there is a lot of it! 

Disk /dev/sda: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0xec1fec1f 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *          63   312560639   156280288+   7  HPFS/NTFS 
 
Disk /dev/sdb: 80.0 GB, 80000000000 bytes 
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x9dc96e9e 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1              63   150191684    75095811   83  Linux 
/dev/sdb2       150191685   156248189     3028252+   5  Extended 
/dev/sdb5       150191748   156248189     3028221   82  Linux swap / Solaris 
salmonowicz@salmonowicz-desktop:~$ cat /boot/grub/menu.lst 
# menu.lst - See: grub(8), info grub, update-grub(8) 
#            grub-install(8), grub-floppy(8), 
#            grub-md5-crypt, /usr/share/doc/grub 
#            and /usr/share/doc/grub-doc/. 
 
## default num 
# Set the default entry to the entry number NUM. Numbering starts from 0, and 
# the entry number 0 is the default if the command is not used. 
# 
# You can specify 'saved' instead of a number. In this case, the default entry 
# is the entry saved with the command 'savedefault'. 
# WARNING: If you are using dmraid do not use 'savedefault' or your 
# array will desync and will not let you boot your system. 
default		0 
 
## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout		3 
 
## hiddenmenu 
# Hides the menu by default (press ESC to see the menu) 
hiddenmenu 
 
# Pretty colours 
#color cyan/blue white/blue 
 
## password ['--md5'] passwd 
# If used in the first section of a menu file, disable all interactive editing 
# control (menu entry editor and command-line)  and entries protected by the 
# command 'lock' 
# e.g. password topsecret 
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/ 
# password topsecret 
 
# 
# examples 
# 
# title		Windows 95/98/NT/2000 
# root		(hd0,0) 
# makeactive 
# chainloader	+1 
# 
# title		Linux 
# root		(hd0,1) 
# kernel	/vmlinuz root=/dev/hda2 ro 
# 
 
# 
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST 
 
### BEGIN AUTOMAGIC KERNELS LIST 
## lines between the AUTOMAGIC KERNELS LIST markers will be modified 
## by the debian update-grub script except for the default options below 
 
## DO NOT UNCOMMENT THEM, Just edit them to your needs 
 
## ## Start Default Options ## 
## default kernel options 
## default kernel options for automagic boot options 
## If you want special options for specific kernels use kopt_x_y_z 
## where x.y.z is kernel version. Minor versions can be omitted. 
## e.g. kopt=root=/dev/hda1 ro 
##      kopt_2_6_8=root=/dev/hdc1 ro 
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro 
# kopt=root=UUID=cd26f71f-2043-4157-93f2-b55c01e3c5f8 ro 
 
## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 
 
## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd1,0) 
 
## should update-grub create alternative automagic boot options 
## e.g. alternative=true 
##      alternative=false 
# alternative=true 
 
## should update-grub lock alternative automagic boot options 
## e.g. lockalternative=true 
##      lockalternative=false 
# lockalternative=false 
 
## additional options to use with the default boot option, but not with the 
## alternatives 
## e.g. defoptions=vga=791 resume=/dev/hda5 
# defoptions=quiet splash 
 
## should update-grub lock old automagic boot options 
## e.g. lockold=false 
##      lockold=true 
# lockold=false 
 
## Xen hypervisor options to use with the default Xen boot option 
# xenhopt= 
 
## Xen Linux kernel options to use with the default Xen boot option 
# xenkopt=console=tty0 
 
## altoption boot targets option 
## multiple altoptions lines are allowed 
## e.g. altoptions=(extra menu suffix) extra boot options 
##      altoptions=(recovery) single 
# altoptions=(recovery mode) single 
 
## controls how many kernels should be put into the menu.lst 
## only counts the first occurence of a kernel, not the 
## alternative kernel options 
## e.g. howmany=all 
##      howmany=7 
# howmany=all 
 
## should update-grub create memtest86 boot option 
## e.g. memtest86=true 
##      memtest86=false 
# memtest86=true 
 
## should update-grub adjust the value of the default booted system 
## can be true or false 
# updatedefaultentry=false 
 
## should update-grub add savedefault to the default options 
## can be true or false 
# savedefault=false 
 
## ## End Default Options ## 
 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cd26f71f-2043-4157-93f2-b55c01e3c5f8 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic 
quiet 
 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cd26f71f-2043-4157-93f2-b55c01e3c5f8 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic 
 
title		Ubuntu 8.04.1, memtest86+ 
root		(hd1,0) 
kernel		/boot/memtest86+.bin 
quiet 
 
### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by caljohnsmith on 2008-09-16
OK, open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following at the end of the file:
```
title	   Windows
root (hd0,0)
makeactive
chainloader +1
```
I think that should be all it takes, but let me know how it goes.

---

### Post by ds1jr on 2008-09-16
Well now it gets further, however whenever I try to boot Windows it tells me that the NTloader is missing. That has to do with Windows I think. It still boots to Ubuntu though. Would this be a lot easier if I switched the drives around and made the drive with Ubuntu on it the master drive? Or would that affect anything.... ??? :confused: Thank you so much for your help!

---

### Post by unutbu on 2008-09-16
ds1jr, perhaps try [http://ubuntuforums.org/showpost.php?p=5247162&postcount=16](http://ubuntuforums.org/showpost.php?p=5247162&postcount=16)
this should restore your NT loader.

caljohnsmith, meierfra, would you happen to know why so many people are finding the NTLDR missing? What action is deleting this file from within the Windows partition?

---

### Post by meierfra. on 2008-09-16
> would you happen to know why so many people are finding the NTLDR missing? 

The most common  causes  for the "NTLDR missing" message:

1.   Menu.lst is referring to the wrong partition ( and  ntldr is not really missing)

2.   ntldr   had been on a partition which seems to have nothing to do with the Windows OS. And this partition was deleted to  install Ubuntu.

---

### Post by ds1jr on 2008-09-18
Thank you soooo much everyone! It works now just like I want it! :guitar: :KS Boots to Windows or Ubuntu at my choice. Thank you so much!

---

