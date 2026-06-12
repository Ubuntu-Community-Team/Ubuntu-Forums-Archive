---
title: "Anyone seen drive designations change randomly?"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by kansasnoob on 2011-01-04
I was trying to help someone understand how to install Ubuntu 10.10 on a two drive setup w/Ubuntu sharing a drive with Windows and noticed that the two drives would randomly change from sda to sdb and vice versa.

Has anyone else seen that happen?

If that happens post installation wouldn't that render both OS's unbootable?

I'd appreciate some help there if possible:

[http://ubuntuforums.org/showthread.php?t=1653686](http://ubuntuforums.org/showthread.php?t=1653686)

I did a brief "recap" in post #20.

I'm actually leaning somewhat towards thinking it might be best in that case to install grub to the pbr of Ubuntu's root partition and then have them use Easy-BCD to boot :confused:

---

### Post by dino99 on 2011-01-04
i've this kind of issue since maverick A2 (grub2 update, was previously well identified)

bios order      //    seen by gparted  //  boot  //   OS
1) HDT (sata)          /dev/sdb            *          Mav & natty
2) ST316 (pata)        /dev/sda                       xp
3/ ST312 (pata)        /dev/sdc                       LTS

so the actual sdb was identified previously as sda (as it might IMO)

this swith have happended in early maverick a2.

---

### Post by wkulecz on 2011-01-04
This has annoyed me since they first started denying that IDE, SATA, & SCSI are actually different.  Logically a drive is a drive, but the differences are real and its a disservice to ignore the mapping I set in the BIOS as to what the drive order should be.

I don't have a solution other than installing grub to all the drives and doing all mounts by UUID in /etc/fstab and the grub2 config files.

---

### Post by dino99 on 2011-01-04
found similar user issue:

[http://ubuntuforums.org/showpost.php?p=10315633&postcount=2](http://ubuntuforums.org/showpost.php?p=10315633&postcount=2)

---

### Post by psusi on 2011-01-04
Yes, this is to be expected.  No, it is not a problem because drives are referenced by UUID instead of device name.

---

### Post by ronparent on 2011-01-04
> Yes, this is to be expected. No, it is not a problem because drives are referenced by UUID instead of device name.
Same observation here. It's annoying but not material!

---

### Post by Kenneth D. Gladden on 2011-01-04
It is a problem when running Virtual Box with raw access to drives.
For example some times when I boot the machine the first drive is 
sda at other times the first drive is sde. Depending on whither the drive is sda or sde Virtual Box will not run

kdgladden

---

### Post by kansasnoob on 2011-01-04
> **psusi said:**
> Yes, this is to be expected.  No, it is not a problem because drives are referenced by UUID instead of device name.

In fstab, yes. But I'd think grub would run into problems (excerpts from a sample grub.cfg):

> insmod part_msdos
insmod ext2
**set root='(/dev/sda,msdos1)'**
search --no-floppy --fs-uuid --set=root b7a0df33-53e4-4f0d-856b-0da92ff0d743


> ### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 10, 2.6.35-22-generic (/dev/sda10) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	**set root='(/dev/sda,msdos10)'**
	search --no-floppy --fs-uuid --set=root 6114df72-5fec-467a-b6cf-bfb49b76def1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=6114df72-5fec-467a-b6cf-bfb49b76def1 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}


I'd personally not seen that before, and I don't want someone to "paint themselves in a corner" with something that will not always boot properly.

---

### Post by kansasnoob on 2011-01-04
> **dino99 said:**
> found similar user issue:

[http://ubuntuforums.org/showpost.php?p=10315633&postcount=2](http://ubuntuforums.org/showpost.php?p=10315633&postcount=2)

Thanks. This is interesting.

---

### Post by psusi on 2011-01-04
> **kansasnoob said:**
> set root='(/dev/sda,msdos10)'

That is a broken grub config since "/dev/sda" is not a valid grub disk name.  Fortunately the next line locates the correct partition by UUID.

---

### Post by kansasnoob on 2011-01-04
> **psusi said:**
> That is a broken grub config since "/dev/sda" is not a valid grub disk name.  Fortunately the next line locates the correct partition by UUID.

That's from my running and bootable Maverick multi-boot:

> lance@lance-desktop:~$ sudo update-grub
[sudo] password for lance: 
Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found Linux Mint 10 Julia (10) on /dev/sda10
Found Debian GNU/Linux (squeeze/sid) on /dev/sda11
Found Ubuntu 10.10 (10.10) on /dev/sda12
Found Peppermint (peppermint) on /dev/sda13
Found Ubuntu 10.10 (10.10) on /dev/sda14
Found Linux Mint Debian Edition (1) on /dev/sda15
Found Ubuntu natty (development branch) (11.04) on /dev/sda16
Found Ubuntu natty (development branch) (11.04) on /dev/sda17
Found Ubuntu 9.10 (9.10) on /dev/sda2
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sda3
done


Since it works I guess it can't really be broken :p

I am however using a newer version of grub2 "1.99~20101126-1ubuntu3", not the newest however.

---

### Post by psusi on 2011-01-04
> **kansasnoob said:**
> 
Since it works I guess it can't really be broken :p


It works because like I said before, the next line locates the correct drive by UUID.

---

### Post by coffeecat on 2011-01-04
Whether or not it's broken, this is a stanza from my non-broken grub:

```
menuentry 'Ubuntu Maverick, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    [COLOR=Red]set root='(hd0,msdos6)'[/COLOR]
    search --no-floppy --fs-uuid --set 49fae418-c360-47e0-85fc-b7208ca28b12
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=49fae418-c360-47e0-85fc-b7208ca28b12 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
```The argument that the next line has a valid UUID so everything is OK falls over, I'm sorry to say. If you have the set root line pointing to the wrong partition, bootup fails. 

This peripatetic naming of sda/b seems to be a real issue.

---

### Post by psusi on 2011-01-04
> **coffeecat said:**
> Whether or not it's broken, this is a stanza from my non-broken grub:

```
menuentry 'Ubuntu Maverick, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    [COLOR=Red]set root='(hd0,msdos6)'[/COLOR]
    search --no-floppy --fs-uuid --set 49fae418-c360-47e0-85fc-b7208ca28b12
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=49fae418-c360-47e0-85fc-b7208ca28b12 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
```The argument that the next line has a valid UUID so everything is OK falls over, I'm sorry to say. If you have the set root line pointing to the wrong partition, bootup fails. 

This peripatetic naming of sda/b seems to be a real issue.

You're not making sense.  Now you are showing a correct root= line with (hd0) instead of /dev/sda, and the search line that follows it changes the root to whatever drive it finds with that UUID, so it does not fall over if the first line is wrong.

---

### Post by kansasnoob on 2011-01-04
I just wish I could reproduce this "drive designation changing" thing so I could see it myself and report a bug properly :p

I've tried adding an extra drive, leaving a usb drive plugged in on reboot, leaving my camera plugged in, etc. But for some reason I always end up with the same device designations, I just can't break my machine :lolflag:

However, I'm convinced that this is largely not an operator error type situation. So I dreamed up a situation to test psusi's theory.

I'll leave both of my drives plugged in, install 10.10 to my testing drive (which is sdb), then shutdown and disconnect sda. Then when I reboot sdb will have to become sda.

At that point I'll know if "updating" grub is necessary to boot. Does that make sense :confused:

---

### Post by 23dornot23d on 2011-01-04
I found the designation changes depending on Cold or Warm boot ......

on a Cold boot ...... on my system ..... disk B then A
but then on a Warm boot ..................  disk A then B

and I find it is consistent ....... but what causes this I am not sure ......


A = internal hard drive .....

B = external USB drive .....

This never fails ...... and as there is a different boot partition on each drive ...... 
I get a different menu each way - so I can easily see what is happening - one has a background picture the other does not.

---

### Post by tgm4883 on 2011-01-04
> **kansasnoob said:**
> I just wish I could reproduce this "drive designation changing" thing so I could see it myself and report a bug properly :p

I've tried adding an extra drive, leaving a usb drive plugged in on reboot, leaving my camera plugged in, etc. But for some reason I always end up with the same device designations, I just can't break my machine :lolflag:

However, I'm convinced that this is largely not an operator error type situation. So I dreamed up a situation to test psusi's theory.

I'll leave both of my drives plugged in, install 10.10 to my testing drive (which is sdb), then shutdown and disconnect sda. Then when I reboot sdb will have to become sda.

At that point I'll know if "updating" grub is necessary to boot. Does that make sense :confused:

grub doesn't care about /dev/sda, /dev/sdb, etc, it cares about hd0, hd1, etc. Thats why you were told that your grub config was broken (although that was incorrect, it was misconfigured not broken), because you had /dev/sda in there. 

In fstab, you shouldn't be mounting drives by using /dev/sda, you should use the UUID. IIRC, this was a change made back in 2007 for 7.04. No need to file a bug as this isn't a bug. 

As for the virtualbox issue, if there isn't a way to specify the disk by UUID then you will likely need to set up a udev rule that will mount the disk at the same location each time (eg. /dev/seagate-500GB), then just have virtualbox access the drive at that location.

---

### Post by tgm4883 on 2011-01-04
> **23dornot23d said:**
> I found the designation changes depending on Cold or Warm boot ......

on a Cold boot ...... on my system ..... disk B then A
but then on a Warm boot ..................  disk A then B

and I find it is consistent ....... but what causes this I am not sure ......


A = internal hard drive .....

B = external USB drive .....

This never fails ...... and as there is a different boot partition on each drive ...... 
I get a different menu each way - so I can easily see what is happening - one has a background picture the other does not.

AFAIK, that is because of your BIOS. You need to set boot order correctly as that is how it is determined which is hd0 and hd1 in respect to grub.

---

### Post by kansasnoob on 2011-01-04
> **tgm4883 said:**
> AFAIK, that is because of your BIOS. You need to set boot order correctly as that is how it is determined which is hd0 and hd1 in respect to grub.

But looking here:

[http://ubuntuforums.org/showthread.php?t=1653686](http://ubuntuforums.org/showthread.php?t=1653686)

The OP indicates that both are internal drives, no USB drives in play at all. So drive designations do appear to change somewhat randomly.

Since I can't reproduce that on my machine I simply want to be sure that I can boot after such a change, like psusi said.

I simply want to see the results myself! 

I mean, I'm trying to instruct someone else about installing Ubuntu, and I want to know for sure that what I'm telling them is accurate.

---

### Post by tgm4883 on 2011-01-05
> **kansasnoob said:**
> But looking here:

[http://ubuntuforums.org/showthread.php?t=1653686](http://ubuntuforums.org/showthread.php?t=1653686)

The OP indicates that both are internal drives, no USB drives in play at all. So drive designations do appear to change somewhat randomly.

Since I can't reproduce that on my machine I simply want to be sure that I can boot after such a change, like psusi said.

I simply want to see the results myself! 

I mean, I'm trying to instruct someone else about installing Ubuntu, and I want to know for sure that what I'm telling them is accurate.

Doesn't matter if they are USB, internal, SSD, IDE, etc. Let me try to explain it in more detail.

In the bios you can set the boot order (hard disk, USB, cdrom, etc). In most BIOS's you can also set the boot order of the hard disks (disk 1, disk 2, disk 3, etc). The first hard drive you set in the BIOS to load will be presented to grub as hd0 (second one will be hd1 and so on). This will not change unless you change the order of the hard disks loading in the BIOS.

When grub loads it sees the disks as hd0, hd1, hd2, etc. grub doesn't know about /dev/sda, /dev/sdb, etc, that stuff happens when the drivers load in the OS.

Once Ubuntu starts to load, the HDD driver loads and populates /dev/ with the hard disk locations (/dev/sda1, /dev/sda2, /dev/sdb1, etc). This is where they can flip flop (they don't flip flop in the BIOS and they don't flip flop in grub). For this reason, you use the UUID to mount it in fstab instead of /dev/sda1. It's better this way not only because it resolves the flip flop issue, but also because you can physically add/remove hard disks without causing mounting problems.

So since the flip flopping happens in the OS and not at the BIOS/grub, you should still be able to boot fine, but it's important to mount via UUID in fstab (the installer mounts it by the UUID for you). Whenever needing to access the drives directly, use the UUID. If it is necessary to not use the UUID somewhere and you HAVE to use a file path, I suggest setting up a UDEV rule based on the UUID to set up a filepath based on that.

---

### Post by wilee-nilee on 2011-01-05
I have noticed this for awhile, using thumbs to boot from. I just open gparted or run fdisk -l to see how the HD is being seen, and have not had a problem when reversed, and I install grub to the sdb mbr which is actually the on board sda but reversed. I know the target partition anyway as I format them myself and custom install like most everybody in this thread at least I suspect.

---

### Post by 23dornot23d on 2011-01-05
> **tgm4883 said:**
> AFAIK, that is because of your BIOS. You need to set boot order correctly as that is how it is determined which is hd0 and hd1 in respect to grub.

This in theory should be what happens ..... BIOS is set to boot from the second drive ........ it should stay like that .


[B]But what actually happens is - the drives swap order ..... 
[/B]
[B]cold boot ....... thats the first boot after power up ..... 
[/B]
with the USB drive always plugged in B then A is the boot order

[B]warm boot ....... reboot without doing a power off 
[/B]
and the drives switch ....... A then B

The USB is plugged in all the time and never removed ,,,,,, so its like having a constant 2 nd drive

---

### Post by kansasnoob on 2011-01-05
Testing completed, and psusi is correct.

I installed a fresh 10.10 on /dev/sdb just choosing the "Entire disc" option which installed grub to the mbr of /dev/sda. So after the initial boot I installed grub to the mbr of /dev/sdb, shutdown the machine and disconnected /dev/sda.

Voila, it still booted just fine even though the device designations had changed:

```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a72d8207-334e-4f18-83e4-6ce433ed1afc
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=a72d8207-334e-4f18-83e4-6ce433ed1afc ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}


lance@lance-desktop:~$ sudo parted -l
Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  76.7GB  76.7GB  primary   ext4
 2      76.7GB  80.0GB  3305MB  extended
 5      76.7GB  80.0GB  3305MB  logical   linux-swap(v1)


```

Regarding the difference between the '(/dev/sdb,msdos1)' and '(hd1,msdos1)' stanzas, it's dependent on the versions of grub-pc and grub-common.

The current Maverick packages use '(hd1,msdos1)', but I'm using a prior Natty version (1.99~20101126-1ubuntu3) and it uses '(/dev/sdb,msdos1)'. I like that version because it lists older kernels as "Previous linux versions" rather than a long list of kernels.

That said I'm not too crazy about the very newest Natty packages.

Many thanks to all :D

---

### Post by Kenneth D. Gladden on 2011-01-17
Why is this thread marked solved? The problem with virtualbox is still there. I do not care which is assigned to the first drive sda, or sde just so it is the same every time the computer is booted. 
kdg

---

### Post by tgm4883 on 2011-01-17
> **Kenneth D. Gladden said:**
> Why is this thread marked solved? The problem with virtualbox is still there. I do not care which is assigned to the first drive sda, or sde just so it is the same every time the computer is booted. 
kdg

Because it is solved. This is a forum, if there is a bug in a particular piece of software, you need to file a bug on that piece of softwares bug tracker. At the very least, file one in launchpad. That being said, as I stated before I believe it is how the BIOS presents the drives in how they are enumerated. So if you cold boot the system, the BIOS might be loading the drives in a different order. Perhaps one of your drives is slower in presenting itself to the BIOS?

---

### Post by psusi on 2011-01-17
> **Kenneth D. Gladden said:**
> Why is this thread marked solved? The problem with virtualbox is still there. I do not care which is assigned to the first drive sda, or sde just so it is the same every time the computer is booted. 
kdg

Because it was explained why this is NOT a problem, but expected behavior.

---

### Post by kansasnoob on 2011-01-17
> **psusi said:**
> Because it was explained why this is NOT a problem, but expected behavior.

+1!

In my particular situation the question was answered, and no abhorrent behavior resulted post-installation. I tested it myself to be sure.

But this had nothing to do with a VM. I certainly agree that having device designations change randomly is not a good thing.

In other words, my "question" was "answered" so it's "solved", that does not mean that the "bug" is fixed :)

---

### Post by tgm4883 on 2011-01-17
> **kansasnoob said:**
> +1!

In my particular situation the question was answered, and no abhorrent behavior resulted post-installation. I tested it myself to be sure.

But this had nothing to do with a VM. I certainly agree that having device designations change randomly is not a good thing.

In other words, my "question" was "answered" so it's "solved", that does not mean that the "bug" is fixed :)

It also doesn't necessarily mean that it is a bug. One might consider it a feature request.

---

