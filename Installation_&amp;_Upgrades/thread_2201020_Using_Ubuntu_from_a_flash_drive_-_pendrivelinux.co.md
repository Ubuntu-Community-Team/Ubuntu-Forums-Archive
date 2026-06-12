---
title: "Using Ubuntu from a flash drive - pendrivelinux.com"
date: 2014-01-22
forum: Installation &amp; Upgrades
---

### Post by Fabzil on 2014-01-22
Hello! ):P

My hard-drive is dying on me, so I want to use Ubuntu from a flash drive because I really don't need speed or power and I can not replace my internal laptop HDD.

I used this tutorial ([pendrivelinux.com]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")) to install the lastest stable Ubuntu .iso to a 16Gb Transcend flash drive.
*ubuntu-12.04.3-desktop-i386 (good checksum)*

As I want to use this install as my main system, I use the options to create a 4Gb **persistent **place of the flashdrive. I don't want to re-install everything every time I use the flash-drive.

Now, the good news is that everything is working fine and when I restart the computer, I can boot on Ubuntu and use it as I please :) :)

**BUT**

after I switch off the computer once, it's impossible for me to start Ubuntu again, the computer can't go further the loading screen. Even if I wait a long time, the computer can't go back to Ubuntu desktop :( :( :(

Can you please help me? My HDD is gonna die one day and I need my Ubuntu back-up up & running!!

---

### Post by oldfred on 2014-01-22
With a 16GB flash drive you can do the installer with persistence or a full install.

       Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

On my 16GB flash drive I installed full Ubuntu but more as a backup boot with 8GB for install and 8GB for data. If full use Lubuntu may be a better choice.

---

### Post by sudodus on 2014-01-22
Persistent live systems are easy to crash. One risk is that you unplug the pendrive before it has finished writing what was stored in RAM during the shutdown procedure. This is particularly difficult if you have a slow pendrive. It is possible that your basic live system is OK, but the casper-rw file containing an overlay file system is damaged. In that case, please try to wipe it and start from the beginning to tweak your system again.

I agree with *oldfred* that it is better to make a full install instead of persistent live system. But it is also sensitive to unplugging the pendrive.

In any case I suggest that you ***back up everything important*** from your internal drive to some other external media (not the system drive) or an internet cloud service (google drive, ubuntu one, dropbox ...)

---

### Post by GrouchyGaijin on 2014-01-22
I have a question about running Ubuntu from an external drive.
Can you plug the drive with Ubuntu installed into a Windows 8 machine and boot Ubuntu or will you run into the secure boot problem?

The thing is I'm thinking of getting a new PC and setting up dual boot with Windows 8.1 seems pretty daunting.
(I really need to run EndNote, which does not work in WINE.)

If I had a USB 3 port that is pretty fast, could I just run Ubuntu from an external drive?

---

### Post by sudodus on 2014-01-22
> **GrouchyGaijin said:**
> I have a question about running Ubuntu from an external drive.
Can you plug the drive with Ubuntu installed into a Windows 8 machine and boot Ubuntu or will you run into the secure boot problem?

The thing is I'm thinking of getting a new PC and setting up dual boot with Windows 8.1 seems pretty daunting.
(I really need to run EndNote, which does not work in WINE.)

If I had a USB 3 port that is pretty fast, could I just run Ubuntu from an external drive?

I think your question is big and important, but different from that of the original poster in this thread, so please start a new thread! (In some computers it is possible to boot a 64-bit Ubuntu USB/DVD system and run it live or persistent live. It will select boot according to the BIOS/UEFI setting. But if you have problems, please don't confuse this thread.)

---

### Post by C.S.Cameron on 2014-01-23
If you use the pendrivelinux method you have linked to you will be limited to 4GB persistence.
Perhaps better to go with a Full install or at least to use persistent partition(s) rather than a persistence file.

---

### Post by Fabzil on 2014-01-24
Omg, I just realized that what I wanted to do is what you call a "full install" and that this persistent stuff is completly different!

So I'm going to do the full install.

I'm sorry but can I ask someone to explain to me what is noatime, journal etc... as talked about it : [Full Install or persistent on Flash-Drives ]("http://ubuntuforums.org/showthread.php?t=2133067")
I know a bit of Ubuntu (used it for like a year, 3 or 4 years ago), and it seems to be an option of the 'mount' console command. BUT I will directly boot on the flashdrive from the start of the computer, so I will undoubtly already mount the device right at the start, right?

Thx you in advance for you help, I will never give up ^^

---

### Post by sudodus on 2014-01-24
You can add ***noatime*** as an option in the system file **/etc/fstab** in the line for the root file system /. See ```
man fstab
```

example:
```

UUID=abc8b4a7-46af-43bd-82fc-030c21ef9887 /               ext4    defaults,***noatime***,errors=remount-ro 0       1
```

Journaling can be switched off in ext4 with ***tune2fs***. See ```
man tune2fs
```

example:
```
sudo tune2fs -O ^has_journal /dev/sdxy
```

where ^ indicates clearing, x is the device letter and y is the partition number, for example **/dev/sdb1**

---

### Post by Fabzil on 2014-01-24
thx you very much subodus, now I understand its some kind of post-process I can do, and I knoow how to do it. Thx you very much. going back to Ubuntu after that much time is hard but I feel it will be better.

So, after my HDD is dying on me, how was the install from a USB to another ? Well, you won't believe me, but the flashdrive that was supposed to receive this install from the LiveUSB just died on me, like tonight xD
I'm cursed!

Anyway, I'll buy an external HDD tomorrow and I'll start over. I guess It's pretty much the same as a flashdrive, except I can make like 3 partitions, 1 for the system, 1 for the swap and 1 for the data.

---

### Post by sudodus on 2014-01-24
Good luck this time :-)

And you might try to revive the pendrive if it is recognized as a device at all: if

```
sudo fdisk -lu
```

can see it as **/dev/sdx**

where x is a device letter a, b or c ...

- Wipe (zeroise) the first megabyte (can be done with [mkusb]("http://ubuntuforums.org/showthread.php?t=1958073"))
- Make a new partition table with ***gparted***

---

