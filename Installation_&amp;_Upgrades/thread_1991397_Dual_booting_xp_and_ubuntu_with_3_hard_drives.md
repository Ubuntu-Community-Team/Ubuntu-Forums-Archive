---
title: "Dual booting xp and ubuntu with 3 hard drives?"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by crazyjust on 2012-05-30
Here is what i'm trying to accomplish. I have 3 hard drives. (1) 80 gb and (2) 500 gb. I would like to install xp on the 80 gb drive, ubuntu on 1 of the 500 gb drives, and have the other 500 gb as a second drive on both xp and ubuntu. I would like to hide the xp drive on ubuntu. I would like to have grub for the boot loader, so I can install burg. I have 4 sata ports on my motherboard 0-3. Can someone please tell me the hookup and steps to accomplish this the correct way? Thanks

---

### Post by oldfred on 2012-05-30
I cannot recommend burg as it is not maintained anymore.

I would install 80GB drive to first SATA port. That should make it be sda and stay as sda. XP's boot.ini is hard coded to a drive and it just is easier if it is sda.  Install Windows and make sure it boots ok.

You can install Ubuntu without disconnecting Windows drive, but have to use Something Else or manual install to get the option to install the grub2 boot loader to sdb, otherwise it defaults to sda and would overwrite the Windows boot loader. Can relatively easily be fixed but still simpler to just to install correctly first.

I prefer smaller / (root) or system partitions. So even on your 500GB drive I would only make / 25GB unless you know you have some very large applications. I have a lot installed and use about 7GB of my 25GB / partition. (I might also reserve another 25GB partition on sdc, see link below).

You can format sdc mostly as NTFS and both Windows & Ubuntu should see it without issue. You can mount the Windows as read only or mount it in / where it will be hidden unless you search for it. Then it will not appear in Ubuntu.

Install differences between versions are minor, once you install Ubuntu to sdb, set BIOS to boot drive that is sdb:
Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

Hide mount examples - better to use UUIDs
sudo mkdir /mnt/windows
UUID=200C11850C1156DE /mnt/windows ntfs defaults,noauto 0 0
or
Hide windows mount with noauto:
sudo mkdir /Windows/sda2
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0

---

### Post by crazyjust on 2012-05-30
Thank you for your quick response oldfred. I don't think I can specify which hard drive to boot from in my bios. It just says sata or ide, and they are all sata. Here is what I did last night. I installed my 80 gb on sata 1, and installed xp. I then shutdown, installed 1 of my 500 gb drives on sata 0, restarted and installed ubuntu. I then shutdown, installed my 2nd 500 gb drive on sata 2, restarted and formatted to ntfs so that both os's see the drive. This seems to work ok, but if I leave it this way, will I encounter any problems? If this way is ok, I will only have to hide the xp drive from ubuntu.

---

### Post by oldfred on 2012-05-30
That way to install should work. Ubuntu uses UUIDs which should not normally change so drive order is not really important. XP's boot.ini has drive & partition in it and that can complicate thing.

If your motherboard supports SATA drives you have to have a boot choice in BIOS. A few very old Dell's with only one SATA port only booted from the IDE drive.

SATA drives do not have jumpers like the old PATA drives. Some BIOS have a sub-menu under hard drive in boot order to choose which hard drive,  and others have another total entry sometimes even a different page in BIOS on hard drive order. Most BIOS also have a one time boot key (f12 on my system) that also gives the choice of boot drives. My USB flash only appears if bootable, plugged in while booting and then it is actually a menu choice under hard drive not USB devices.

Windows boot loader in sda will not boot Ubuntu, but I prefer to leave the Windows boot loader in sda, so if sdb fails, you can still boot sda (and vice-versa).

---

### Post by crazyjust on 2012-05-30
Ok. I will leave it as is then. Thank you very much oldfred.

---

