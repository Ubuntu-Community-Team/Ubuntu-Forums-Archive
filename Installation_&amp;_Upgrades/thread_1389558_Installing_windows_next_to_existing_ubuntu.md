---
title: "Installing windows next to existing ubuntu"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by BramWillemsen on 2010-01-24
Hi everyone,

The last week i installed a virtualized Windows inside ubuntu using VirtualBox. The performance of certain programs is a bit poor unfortunately. Therefore i would like to install Windows next to ubuntu on my laptop (dual boot environment). 

Right now ubuntu uses the entire harddisk. Is it possible to safely allocate some space for a windows install? And if i install windows, will grub still automatically boot when the computer starts ? 

kind regards,

Bram

---

### Post by phillw on 2010-01-24
Hi,  yes and no ....

It is quite okay to set aside some room for Win - just use GParted from the Live CD.

When you install your Win, your grub will get over-written. Your ubuntu area will be quite safe & you can pop Grub back on by following the instructions over here --> [Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")  That will get you back dual booting.

Regards,

Phill.

---

### Post by kansasnoob on 2010-01-24
What version of Windows? 

What version of Ubuntu?

The output of following commands from Ubuntu would be helpful:

```
lsb_release -a
```

```
grub-install -v
```

```
sudo fdisk -l
```

BTW that's a lower case L.

```
df -H
```

---

### Post by BramWillemsen on 2010-01-24
Thanks for your suggestion PhilW. And thanks KansasNoob! I posted the output below


```
lsb_release -a
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

```
grub-install -v
```
grub-install (GNU GRUB 1.97~beta4)

```
sudo fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80d2f3ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         608     4883728+  82  Linux swap / Solaris
/dev/sda2   *         609       19457   151404592+  83  Linux


```
df -H
```
/dev/sda2              153G    52G    94G  36% /
udev                   920M   287k   919M   1% /dev
none                   920M   725k   919M   1% /dev/shm
none                   920M   316k   919M   1% /var/run
none                   920M      0   920M   0% /var/lock
none                   920M      0   920M   0% /lib/init/rw

---

### Post by phillw on 2010-01-25
Hi, yes, you're running 9.10 & Grub2, so you'll want those instructions from the thread I posted to get Grub back after your Win install.

You've got 93GB free on your sda2 partition to slice and give to Win (About 20 - 25 GB is plenty, if you want to put a couple of programmes and associated data on it.)

Easy to set it up (must be a primary partition, so set it as sda3) and format it as NTFS, assuming you're putting on XP / Vista / Win7. 

Your Ubuntu installation will be able to read and write to the NTFS area, but Win will not 'see' you Ubuntu area.

Don't forget anti-virus & spyware protection for your Win area !! 

If you intend on downloading files to your ubuntu area and then copying them over to your Win area, you <i>may</i> want to consider putting a check-system for such files onto your Ubuntu area - I cover one such, Bitdefender, over here --> [http://www.vpolink.com/forums/99-Security-Stuff](http://www.vpolink.com/forums/99-Security-Stuff) Along with some general tightening up of FireFox for both Win & Ubuntu.

Regards,

Phill.

---

### Post by BramWillemsen on 2010-01-26
Dear PhillW,

Thanks for your suggestions. So i run GParted from the liveCD to slice of a part of the SDA2 partition to form a new SDA3 NTFS partition. When i run the windows installer i will be able to select this small partition and afterwards i will restore the GRUB bootloader by using the liveCD and the instructions you gave me before.

Do you think there is any risk if the instructions are followed and read carefully? The reason is that if the ubuntu partition would somehow get damaged, it would be really troublesome.

kind regards, Bram

---

### Post by howefield on 2010-01-26
> **BramWillemsen said:**
> Do you think there is any risk if the instructions are followed and read carefully?

There is always risk when you carry out such work on a hard disk, however, it should be fairly small.

Do back up your data properly before hand though, if you haven't already.

Just out of interest, did you ascertain why your programs were running slowly in your virtual machine ? Was it a lack of hardware resources to run two simultaneous operating systems, or something else ?

---

### Post by BramWillemsen on 2010-01-26
I think it is a lack of hardware resources. my laptop CPU is not too powerful (AMD Turion 2000mhz dual core). I did allocate enough memory but certain trivial processes were just running very slow.I'm talking about firefox and the program called Marratech that plays back a recorded lecture at the university. The latter just runs way too slowly, the video can't play and the sound is broken down because it can't be processed quick enough. I did allocate 512MB ram but unfortunately i chose for using expanding disk size in VirtualBox instead of a fixed partition (not sure if this is the bottleneck) I'm kind of confident that running dual boot would make it run at a more decent speed.

---

