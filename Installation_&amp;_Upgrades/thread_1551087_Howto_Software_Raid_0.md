---
title: "Howto: Software Raid 0"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by urbanus on 2010-08-11
[SIZE="5"]**Guide**[/SIZE]

*This is how I managed to create a Raid 0 setup!*

**My "specs":**
- Linux Mint 9 (shouldn't matter, and I don't have a username there)
- 2 x 298 GIG hdd's
- **Backup etc!! **


**1.**
Boot into the live cd (Ubuntu, kubuntu, Linux Mint, all should work...I think)

**2.**
Install "mdadm" and remove "dmraid" (the latter causes some of my drives to not show up in the installer).
> sudo apt-get update
sudo apt-get install mdadm
sudo apt-get remove dmraid

**3.**
Partitioning the two (or more?) drives:
- Start a partitioning manager you like (gparted?)
- Create a 500 MB partition on the "first" drive ("/dev/sda" + "/dev/sdb" = "/dev/sda" is the first one, but you can use any...I think)
- Create the main ("/") partition on both drives, it's size should be the rest of the free space minus the space used in the above partition and the swap partition beneath. Remember, this and the next partitions needs to be of equal size on both drives.
- The next partition is for your swap space. Create them with the same size as your RAM (combined they then will become doubled the space of your RAM).

*It's important you are aware what partitions are what "names", sdb1 etc. You can also use different partitions sizes off course, as long as they have "enough" space.*

**4.**
Create the raids:
> sudo mdadm --create /dev/md0 --verbose --level=0 --raid-devices=2 /dev/sda2 /dev/sdb1
sudo mdadm --create /dev/md1 --verbose --level=0 --raid-devices=2 /dev/sda3 /dev/sdb2

Further explanations are found in my sources (first one), but basically we pair up the partitions on each hdd. "--level=0" is where we choose to use raid 0, just sayin :-)

**5.**
Format the new raids, or else the install application will want to alter the partition table, on the swap raid partition at least in my experience.
> sudo mkfs.ext4 /dev/md0
sudo mkswap /dev/md1

**6.**
Start the installer (on the desktop), but **DON'T** reboot in the end when it asks!!!
- Complete the steps...
- ...until you get to the partitioning, choose the advanced option at the bottom.
- Choose "/dev/md0" and click change, choose ext4 (or what ever you want) in the dropdown menu, choose to format and choose mount point "/".
- Choose "/dev/md1" and click change, choose swap (now the rest is greyd out?)
- Choose the 500MB partition, click change: ext4, format, "/boot"
- **IMPORTANT!** When you arrive at the summary page (after entering name, password etc), click advanced at bottom right, and choose the drive where the 500MB partition is located ("sda", "sdb" etc....but NOT "sda1", "sdb1" etc), this is where grub, the boot loader, will be installed.
- The pair partitions will show in black as unknown with a warning sign...just ignore this, it's ok (assuming the drives doesn't have additional problems).

*You can skip the step on the summary page, but then the Ubuntu installer will install the boot loader on what ever drive it considers the first drive. This should be technically ok, but I prefer to keep Linux separate, had the Win7 connected, so it was detected by Grub.*

**7.**
We now need to do some stuff on the installed Linux, but before we boot off it because it can't boot before we do. So we will mount it and "log" into it.
> sudo mount /dev/md0 /target/
sudo mount --bind /dev/ /target/dev/
sudo mount --bind /sys/ /target/sys/
sudo mount --bind /proc/ /target/proc/
sudo mount --bind _/dev/sda1_ /target/boot/
sudo chroot /target

Notice the underlined part, you have to point it to the 500MB partition you created.
**IMPORTANT: In Ubuntu 11.04, use the mounted dir, and not /dev/sda1.**
*"/media/7feb0b41-e0c2-4d98-b83e-f5f8f7b2e94b" <- example*

> sudo apt-get update
sudo apt-get remove dmraid
sudo apt-get install mdadm
sudo grub-install _/dev/sda_

Again, notice the underlined part, do the same as above, where is the 500MB partition?
**Update:** Notice that "dmraid" is now removed. A bird told me that it could interfere with mdadm. I installed/kept it, but you should probably remove it. Please tell me if this messes up things!
**Update 2:** Ubuntu 11.04 doesn't have dmraid, so nothing to remove :-)

**8.**
Reboot and remove the live cd/usb stick. If you have set the BIOS to boot from the correct HDD, your Linux Raid 0 setup should start :-)


Any questions?


_Sources/inspiration:_
[http://blog.foobaria.com/2010/05/installing-ubuntu-1004-desktop-with.html](http://blog.foobaria.com/2010/05/installing-ubuntu-1004-desktop-with.html)
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by dino99 on 2010-08-12
good thread, thanks

but need to be moved to subforum "tutorials & tips" for better needs

---

### Post by urbanus on 2010-08-12
ok, will do so as soon as I find out how :-)

---

### Post by realzippy on 2010-08-12
For those not liking the command line,software RAID
can be set up easily with the GUI during installation/partitioning with the
*alternate* CD...

---

### Post by urbanus on 2010-08-12
I actually noticed that the guides usually talked about the alternate CD, but I was SO close to getting it right when I noticed it :-P

Here is a guide using the alternate CD and GUI:
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by trendle on 2010-08-12
Hi,
I'm curious.
Why do you re-install dmraid at the end of the process after removing it at the start.

Isn't dmraid superfluous if you are using mdadm ?
I thought it was for fakeraid cards that have actually been set up to run raid.  If you use the card as a normal expansion card with no raid features, then I thought you would not need dmraid.
Please correct me if I'm wrong.:confused:

regards
Trendle

---

### Post by urbanus on 2010-08-12
You're right, and it's easy! 

I tried a lot back and forth, so parts of this how to can be done differently. I started working on this say 6 pm, and found the working solution around 3 am ;-)

So in conclusion, dmraid probably doesn't make any difference in retrospect :-)

The important thing is to create a separate partition thats not part of the raid, and to in the end mount it before one restarts and run the grub-configure to set up grub and the /boot partition properly.

---

### Post by trendle on 2010-08-13
I'm no expert... but in my trawling of the forums about raid problems, there seems to some concern about mixing dmraid and mdadm.  So I might not say '*dmraid probably doesn't make any difference in retrospect*' since it might if it is reinstalled.

Apparently dmraid is now installed by default whereas previously it wasn't.

So I think that users not using fakeraid off their SATA cards or Motherboard, wishing to install **mdadm raid** would be best to just leave dmraid out after uninstalling it, as you suggest at the beginning of your useful guide.

---

### Post by urbanus on 2010-08-13
I will update my guide!

But I also realized that I uninstall it from the live CD session, but not the actual installation. So I will make a simple "remove" change.

---

### Post by urbanus on 2011-07-27
Wohoo! My guide made it onto reddit and r/linux via a blog :D

"Forward source": [http://www.reddit.com/r/linux/comments/j103q/installing_ubuntu_onto_software_raid_0/](http://www.reddit.com/r/linux/comments/j103q/installing_ubuntu_onto_software_raid_0/)

---

### Post by itzfritz on 2011-12-08
Some notes for Ubuntu/Mint >=11.04:
- you (may) need to mount your 500MB /boot partition before using it in your chroot environment, else get an error "mount: Not a directory"
```

sudo su
u=blkid -o value -s UUID /dev/sda1
mkdir /media/$u
mount -t ext4 /dev/sda1 /media/$u
mount --bind /media/$u /target/boot

```
- you (may) also need to bind /dev/pts into your chroot:
```

for f in sys proc dev dev/pts; do mount $f /target/$f; done

```
 HTH

---

