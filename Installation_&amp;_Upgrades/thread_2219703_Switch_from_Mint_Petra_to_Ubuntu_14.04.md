---
title: "Switch from Mint Petra to Ubuntu 14.04"
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by The_Clowd_Kraut on 2014-04-25
I am almost new to Linux and played with different live CDs. After a while I installed Linux Mint 'Petra' on my PC, but in the end I don't like it and want to use Ubuntu 14.04. 

So, I used a USB stick to boot and install it on /sda. Before installation I formatted /sda. It all worked fine, no error messages at all. 

Then I restarted and saw in the boot menu:

```
Ubuntu
 Erweiterte Optionen für Ubuntu
 Memory test (memtest86+)
 Memory test (memtest86+, serial console 115200)
 Linux Mint 16 Petra (16) (auf /dev/sdb1)
 Erweiterte Optionen für Linux Mint 16 Petra (16) (auf /dev/sdb1)
```

Okay, some remainings, so I start Ubuntu... and nothing happens. The screen stays black.

When I choose Linux Mint it still starts and works.

What can I do to fix this?

(Singing "I want my U-bun-tu" to the Dire Straits melody of "I want my MTV") :guitar:

---

### Post by The_Clowd_Kraut on 2014-04-25
Second try. 

I booted from the USB again, and during installation I formatted sda and sdb, told Ubuntu to use sda mainly. 

Result: 

Alert! dev/disk/by-uuid/"number of the disk" does not exist. 
Dropping to a shell!

And then there is:

(initramfs) 

I tried to "mount sda".

Result: 
can't read '/etc/fstab': no such file or directory. 

Did I kill this PC? #-o

---

### Post by The_Clowd_Kraut on 2014-04-25
Third try. I read about boot-repair and hope to use it to fix this mess. Trying to install it, following the official documentation on this site.

Result: 

```
Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages)  404 Not Found

Some index files failed to download. They have been ignored, or old ones used instead.
```

Nothing works as it should.

---

### Post by The_Clowd_Kraut on 2014-04-25
Try 4. 

Using the grub command line. After finding out which is the other name of the boot disk:

```
[FONT=monospace]set root=(hd0,msdos1) 
[/FONT][FONT=monospace]linux /vmlinuz root=/dev/sda ro
[/FONT][FONT=monospace]initrd /initrd.img 
[/FONT][FONT=monospace]boot [/FONT][FONT=monospace]
[/FONT]
```

Result:

```
Gave up waiting for root device. ....

ALERT! /dev/sda does not exist.
```

---

### Post by fantab on 2014-04-25
Post more details about your computer and the hardware inside it, like RAM CPU Graphics No. of HDDs/SSDs etc.
"Try Ubuntu without installing", open Terminal [ctrl+alt+t], post the output of the following;
```
sudo parted -l
sudo fdisk -l
```

---

### Post by The_Clowd_Kraut on 2014-04-25
DFI ultra NF4 mainboard
3GB Ram
AMD CPU 64 X2 Dual Core 3800+ x2

Onboard Raid decativated in Bios
IDE Masters and Slaves decativated in Bios (one old IDE is plugged in but will be used later)

4 identical SATA disks: 

sda
sdb
sdc
sde

If I choose to do "something different" in the installer I can see that one disk - the first - is shown like this:

/dev/mapper/nvidia_dajcfdae
/dev/mapper/nvidia_dajcfdae1  ext4
/dev/mapper/nvidia_dajcfdae5  swap
/dev/mapper/nvidia_dajcfdae    ext4

The others are shown as /dev/sdx etc.

I heard that these mapper or LVM things can cause trouble when setting up Ubuntu on a Raid, but the Raid is switched off, the disks should behave like normal disks.

---

