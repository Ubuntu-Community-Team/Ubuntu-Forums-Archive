---
title: "GRUB problem when adding HDD"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by Lage on 2007-03-30
Hello.
I have a problem with GRUB when adding a new hard drive to my system. I have been checking around but haven't found any post that describes just my problem.

I run a double-boot system with Ubuntu 6.10 and Windows XP. My HDD setup is thus:

* One IDE disk with a Windows partition, connected to the first IDE channel.
* One IDE disk connected to the second IDE channel
* One SATA disk connected directly to motherboard, containing one NTFS partition, one Linux swap partition and the partition with Ubuntu

The problem arises when trying to add another IDE disk to the second IDE channel. The two disks on this cable are identical, and each of them runs fine under Windows. Only when connecting both at once does GRUB give me "Error 22". It doesn't matter which disk is connected to which connector on the cable either; I have tried all four possibilities and also changed master/slave jumper settings.

At first I thought GRUB was installed on the SATA disk (where the Ubuntu partition is), but having disconnected this disk, thinking I might be able to start Windows XP without GRUB, GRUB still loaded. I hence conclude GRUB is loaded from the same disk as Windows.

What do I need to do to make GRUB load correctly?

---

### Post by elints on 2007-03-30
Have you set the master, slave, cable select jumpers on both drives?

---

### Post by 1/0 on 2007-03-30
You should be able to see which drive grub is installed on in /boot/grub/menu.lst

Also, the master/slave setting of the jumpers on the drives are critical.

---

### Post by 1/0 on 2007-03-30
Beat me with a minute... 

It could be that the drive labels has switched. In that case you should change the (hd0,0) and root=/dev/hda1 in /boot/grub/menu.lst 

If its the first partition on second drive it should be (hd1,0).

Edit: you can also check by:

```
sudo fdisk -l
```

---

### Post by Lage on 2007-03-30
I thought I had tried all possible master/slave combinations, which I mentioned in my original post. However, setting the disk that was originally there (on the secondary IDE channel) to master, it will only work with one of the connectors on the cable, otherwise giving error 21 (NB: not 22).

I still can't understand why two disks, neither of which contains an operating system or is even on the same channel as any of the disks containing operating systems, would mess up the boot loader?

I also tried running fdisk from the Ubuntu Live CD, first without connecting the extra drive and then after connecting it again. The *only* change is that I now have a hdd1 in addition to the disks I had before. The disk configuration now looks such:

/dev/sda1 - NTFS partition (on the SATA disk)
/dev/sda2 - Linux swap partition
/dev/sda3 - Linux partition, containing Ubuntu

/dev/hda1 - NTFS partition, containing Windows
/dev/hda2 - NTFS partition

/dev/hdc1 - NTFS partition

/dev/hdd1 - NTFS partition (the one just added)

It may be worth mentioning that hda1 and hdc1 both have an asterisk in the "Boot" column, while none of the others has. I don't know what this means.

---

### Post by confused57 on 2007-03-30
> **Lage said:**
> I thought I had tried all possible master/slave combinations, which I mentioned in my original post. However, setting the disk that was originally there (on the secondary IDE channel) to master, it will only work with one of the connectors on the cable, otherwise giving error 21 (NB: not 22).

I still can't understand why two disks, neither of which contains an operating system or is even on the same channel as any of the disks containing operating systems, would mess up the boot loader?

I also tried running fdisk from the Ubuntu Live CD, first without connecting the extra drive and then after connecting it again. The *only* change is that I now have a hdd1 in addition to the disks I had before. The disk configuration now looks such:

/dev/sda1 - NTFS partition (on the SATA disk)
/dev/sda2 - Linux swap partition
/dev/sda3 - Linux partition, containing Ubuntu

/dev/hda1 - NTFS partition, containing Windows
/dev/hda2 - NTFS partition

/dev/hdc1 - NTFS partition

/dev/hdd1 - NTFS partition (the one just added)

It may be worth mentioning that hda1 and hdc1 both have an asterisk in the "Boot" column, while none of the others has. I don't know what this means.

You might want to boot into Ubuntu & post the output of:
```
cat /boot/grub/menu.lst
```
this might reveal what's going on, it's probably something to do with your hard drive boot order in bios

---

### Post by Lage on 2007-03-30
Thanks to you all; I really appreciate the help and ideas.

menu.lst is an awfully long file. I won't paste everything in, but as I can't figure out exactly what is useful information, I have included some commented stuff as well:


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
# kopt=root=UUID=3f9c9e57-d333-4470-a69c-f32ecfff70bc ro
# kopt_2_6=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,2)

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd2,2)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd2,2)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd2,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd2,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd2,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by Lage on 2007-03-30
Oh, by the way... almost forgot. I checked the BIOS for HDD boot order. It is:

1. Primary Master (the one with Windows, hda)
2. Secondary SATA Master (the one with Linux, sda)
3. Secondary Master (the one which has been there all the time, hdc)
4. Secondary Slave (the newly added one, hdd)

---

### Post by confused57 on 2007-03-30
> **Lage said:**
> Oh, by the way... almost forgot. I checked the BIOS for HDD boot order. It is:

1. Primary Master (the one with Windows, hda)
2. Secondary SATA Master (the one with Linux, sda)
3. Secondary Master (the one which has been there all the time, hdc)
4. Secondary Slave (the newly added one, hdd)

I should have also asked you to post the output of:
```
cat /boot/grub/device.map
```

With your current bios hard drive boot order, your Window's drive should be (hd0) and your Ubuntu drive (hd1)...meaning your Ubuntu root partition would be (hd1,2).

If you get a grub menu at boot, you could try highlighting your Ubuntu entry, press "e", then change root to (hd1,2), then press "b" to boot...just to see if it will work, this change is only temporary, though.

Added:  Your easiest solution may be to set your bios hard drive boot order according to the results of your device.map results.

---

### Post by Lage on 2007-03-30
OK, now things are getting *really* interesting! =)

device.map looks like this, when having booted Ubuntu with the three original disks:

(hd0)   /dev/hda
(hd1)   /dev/**hde**
(hd2)   /dev/sda

However, fdisk only shows:

/dev/sda1
/dev/sda2
/dev/sda3
/dev/hda1
/dev/hda2
/dev/hdc1
, which gets me really confused! Where did the **hde** come from? And where did hdc go?

Do I get the following right?
In order to edit menu.lst, I need to be able to boot Ubuntu, i.e. I cannot add the extra hard drive. However, in order to know how that disk is named, they both need to be attached. Catch 22. (Not referring to *error* 22.)

As for the idea of adjusting the boot order in the BIOS, it sounds like an easy idea, but the same problem applies here: I don't know what "name" the new disk has, since I can't load Ubuntu as long as it is connected--that is, unless I disconnect the other one.

Gosh, I do feel like a real newbie asking these questions, but I really haven't got the hang of this kind of low-level configurations yet!

---

### Post by confused57 on 2007-03-30
Isn't there some way to differentiate the drives in your bios hard drive boot order? For example:
#1--master hard drive on IDE controller#1(hda)
#2--master hard drive on IDE controller#2(hde) or (hdc)?
#3--SATA drive
#4--slave drive on IDE controller#2(hdd)

Your master drive on IDE#1 was probably recognized as hde when you installed Ubuntu, I think that is when your device.map is created & doesn't automatically change  later.

It "should" work if you can find a way to get your bios boot order as I've listed above...

---

### Post by confused57 on 2007-03-30
What you might want to try is to install grub to your SATA drive mbr, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
just have the 3 drives connected the way you did when you installed Ubuntu, for example:
```
sudo grub
find /boot/grub/stage1
root (hd2,2)  <-----the above command should return this, then
root (hd2,2)
setup (hd2)
quit
```

then connect your 4th hard drive & set your bios hard drive boot order for SATA drive first, the Window's drive 2nd...you should get a grub menu, highlight your Ubuntu entry, press "e", change root to (hd0,2), then press "b" to boot...if this works, it's only temporary and you can make it permanent in your /boot/grub/menu.lst.  You might need to reconfigure your device.map to show:
(hd0) /dev/sda
(hd1) /dev/hda

An entry similar to this should boot your Window's drive:
```
title              Windows XP
rootnoverify       (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

You may not want to set your system up this way, but it "might" be an option to consider, or not.

---

### Post by Lage on 2007-04-02
Many thanks to all of you, and especially to confused57. As a matter of fact, it seems like the disk in question seems to be a bit messed up otherwise as well... so I'm not sure wherein the problem lies any more. I will try your recommendations however. Too bad I'm short of time before I'm going away for two weeks. Hey, the good thing is, at least I won't need the hard drive while I'm not at home!

---

### Post by pixelpainter on 2007-04-02
Instead of slecting Master and slave jumper combinations... try using the cable select for both drives... I had similar problem and it worked for me :)

---

### Post by pixelpainter on 2007-04-02
Instead of slecting Master and slave jumper combinations... try using the cable select for both drives... :)


Sorry about double post... I don't know how to delete it :(

---

### Post by Lage on 2007-04-03
> **pixelpainter said:**
> Instead of slecting Master and slave jumper combinations... try using the cable select for both drives... I had similar problem and it worked for me :)
Yes, I did try that. It didn't work, unfortunately. I tried both master/slave combinations, cable select, and I tried exchanging the cable for another one. Still nothing works. Like I said, there must be something else wrong with the disk--which is weird, since it worked fine alone just last week...

---

### Post by 1/0 on 2007-04-03
Check the drive. Usually the manufacturer has some control program (s.a. SeaTools for Seagate). That way you can check if the drive is faulty but this sounds like a GRUB misconfig/install.

It could be that GRUB designates different names for the partitions then the kernel. When you boot go to the command line in GRUB by pressing "c". Then type **root (hd** and tab (maybe just ( and tab). You should see your disks. Complete the rest (hd0,x) for each drive. Write it down. Then edit /boot/grub/device.map so that GRUB points at the correct drives. Update menu.lst and reinstall GRUB in the MBR.

Does that help?

---

### Post by pixelpainter on 2007-04-03
If you are interested, there is an excellent program called Acronis Disk Manager, and I think they have a trial too. Once installed u can make an Acronis boot disk. Once booted in you can check out partition info such as hdd and partition #'s, (and also check for partition errors) also u can access just about any OS partition and edit text files (I used this to edit my boot.ini file while switching partitions around) and copy any files to any other os partition. I have found this to be one of the most useful utilities I have ever owned, especially when it comes to stuff like this. Because you are accessing pre-os boot there are no issues with locked hdd's. You can change, create, format, resize any partition and also change active partition.
Anyway... this utility may help you find out some of the info u need or help you trouble shoot errors.

BTW this is a windows program :)

---

### Post by Lage on 2007-04-20
Allright, I'm back in town and yesterday and today I have been messing around with my computer to see if I can get things right. 

Some interesting facts have arisen, but unfortunately also a new problem, which I really need fixed.

The facts:

1. Checking the (Seagate) disk with SeaTools didn't reveal a single problem. So the disk itself isn't the problem.

2. Depending on jumper settings and where the disks are placed on the cable, sometimes one shows up in BIOS, sometimes none, and sometimes both. Replacing the IDE cable (which was brand new, BTW) seems to increase the chance of both showing up. I have no explanation to this, but I'm just sticking with whatever works best (or least bad).

3a. The S-ATA disk seemed to change from (hd2) to (hd3) when attaching the new disk. Changing this in menu.lst now makes it possible to boot Ubuntu! :KS  Yay.
3b. Changing boot order in BIOS so that the S-ATA disk gets first priority changes the S-ATA disk to being (hd0), while the Windows disk becomes (hd1).

4. Ubuntu now boots fine, but when trying to boot Windows, it says "NTLDR missing, press Ctrl-Alt-Del to reboot." Interestingly, setting the Windows disk to first priority in BIOS, Windows starts fine and GRUB is not loaded--however, Windows does not recognise the new IDE disk. (It might not have been recognised by BIOS either this time, who knows? Each time BIOS setup is exited, the computer reboots so there is no way to tell whether all disks have been recognised at a certain boot-time.)

Browsing the web for the NTLDR problem, I find all kinds of solutions, but neither seems to regard the kind of setup I have. What can I do? :confused: I will more than gladly do anything except re-install either of the operating systems. Unfortunately this problem seems to be able to arise for a number of reasons, but I thought my setup might give a clue as to what's wrong.

---

### Post by confused57 on 2007-04-20
If I understand correctly, you're able to boot your Ubuntu sda drive by selecting it as the first hard drive booted in bios...this would make this (hd0), as you found out, and necessary changes need to be made to your menu.lst, i.e. root (hd0,2).  If your Window's drive is identified as (hd1), then you can try changing your device.map:
```
gksudo gedit /boot/grub/device.map
```
then change the drive order:
```
(hd0) /dev/sda
(hd1) /dev/hda
```

you could include your other drives in device.map, but if the above is correct and you're not booting to the other 2 drives, you "shouldn't" need an entry for them.

Then add an entry to boot Windows similar to the one in the 3rd link in my signature.

---

### Post by Lage on 2007-04-23
Thanks a million! I have finally got it to work just the way I wanted it! :KS 

Interestingly, setting (hd0) to represent /dev/sda and (hd1) to represent /dev/hda in device.map works when setting hda to boot before sda, but having swapped the order, the sda suddenly is (hd2) and both operating systems boot fine (although Ubuntu now has to boot from (hd2,2) instead of (hd0,2). That is, however, before attaching the new disk.

Having attached the new disk, setting the hda to boot first will not even start GRUB, which instead states the now well-recognised Error 22. However, setting the SATA disk to boot first, this is what happens:
* Booting Ubuntu still works fine, from (hd0,2).
* Trying to boot Windows again states that NTLDR is missing. So, just as confused57 suggested, I changed the "root" entry under the Windows boot option to "rootnoverify", and, in addition to this added the "map (hd0) (hd1)" and "map (hd1) (hd0)" lines. This did the trick! Now Ubuntu boots just the way it should, and so does Windows!

The only questions I now have left are out of curiosity: What does the map command actually do? I can clearly see that it somehow changes places between (hd0) and (hd1). Does this trick Windows into thinking that it boots from the "first" hard drive, because it simply refuses to boot from any other disk? And secondly, what difference does the change of "root" for "rootnoverify" make?

---

### Post by confused57 on 2007-04-23
> **Lage said:**
> Thanks a million! I have finally got it to work just the way I wanted it! :KS 

Interestingly, setting (hd0) to represent /dev/sda and (hd1) to represent /dev/hda in device.map works when setting hda to boot before sda, but having swapped the order, the sda suddenly is (hd2) and both operating systems boot fine (although Ubuntu now has to boot from (hd2,2) instead of (hd0,2). That is, however, before attaching the new disk.

Having attached the new disk, setting the hda to boot first will not even start GRUB, which instead states the now well-recognised Error 22. However, setting the SATA disk to boot first, this is what happens:
* Booting Ubuntu still works fine, from (hd0,2).
* Trying to boot Windows again states that NTLDR is missing. So, just as confused57 suggested, I changed the "root" entry under the Windows boot option to "rootnoverify", and, in addition to this added the "map (hd0) (hd1)" and "map (hd1) (hd0)" lines. This did the trick! Now Ubuntu boots just the way it should, and so does Windows!

The only questions I now have left are out of curiosity: What does the map command actually do? I can clearly see that it somehow changes places between (hd0) and (hd1). Does this trick Windows into thinking that it boots from the "first" hard drive, because it simply refuses to boot from any other disk? And secondly, what difference does the change of "root" for "rootnoverify" make?

Great to know you got everything working, your perseverence paid off...you're right that the mapping commands fools Window's into thinking it's the first OS, which it needs to be to successfully boot.  My understanding is that rootnoverify instructs grub to not attempt to mount the partition, which frequently works when using just root doesn't..  See the first link in my signature for some excellent explanations on grub & bootloaders.  Thanks for the update.

---

