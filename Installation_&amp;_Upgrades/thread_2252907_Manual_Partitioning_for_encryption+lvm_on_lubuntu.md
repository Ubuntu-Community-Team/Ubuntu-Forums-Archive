---
title: "Manual Partitioning for encryption+lvm on lubuntu?"
date: 2014-11-15
forum: Installation &amp; Upgrades
---

### Post by TheFu on 2014-11-15
While reloading a netbook with Lubuntu 14.04.1 the last few days, I've struggled and been unable to manually setup the partitioning in a way I wanted.

Want to use whole install encryption, make the /boot partition 1G and have the swap at 4G.  The defaults are too small for /boot and swap to be useful. The defaults are just too small.

So after trying to install about 8 times, it seems there isn't any way to convince Lubuntu's installer to let me tweak those settings. What am I missing?

I tried the "do something else" and it would never let me add VGs to the encrypted partition - so the root-vg coudn't be created, and the install had to be canceled.

Did boot into a liveCD and created the partitioning + LVM the way I wanted, but the installer refused to honor those, insisting on wiping the disk.

Is there a way to accomplish what I need?

---

### Post by oldfred on 2014-11-15
Herman has several pages on LVM installs, slightly older version, but I would expect it is the same.
Never used LVM nor encryption.

[URL="http://members.iinet.net.au/~herman546/index.html"]http://members.iinet.net.au/~herman546/index.html

[/URL] The Performance Impact Of Linux Disk Encryption On Ubuntu 14.04 LTS - std vs. full disk LVM or encrypted /home
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_encryption&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_encryption&num=1)
14.04 Encrypt LVM install with dual boot Windows 8 UEFI/gpt- dusf
[URL="http://ubuntuforums.org/showthread.php?t=2218477"]http://ubuntuforums.org/showthread.php?t=2218477
[/URL]
 LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

[URL="http://ubuntuforums.org/showthread.php?t=2218477"]
[/URL]

[URL="http://members.iinet.net.au/~herman546/index.html"]
[/URL]

---

### Post by TheFu on 2014-11-16
Thanks. However, when doing whole partition encryption, LVM happens "inside" the encrypted volume/partition.  There was no way to get to any LVM control during the setup ... or I missed it somehow.

I suspect there is a known workaround that isn't as hard as this: [https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions) 

One of the things that bothers me is I specifically made a GPT disk, but the wizard wiped that, created an MBR and logical partitions.  OTOH, it is easy to complain and much harder to make things like this flexible, but prevent foolish inputs.

This laptop is used for travel, so not having it encrypted is unacceptable. Not having enough swap leads to unexpected crashes. Had it set to 2G over the summer and it crashed weekly before making it 4G.

---

### Post by oldfred on 2014-11-16
Much of this is back when we had the alternative installer. Not sure how it now changes.

But all the auto install options always create their own default partitions. Only with Something Else can you control that. And with Something Else is full drive encryption even available? 

 How to: Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)
[http://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](http://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu)
[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

---

### Post by TheFu on 2014-11-16
It is possible to setup encrypted partitions, but I haven't found the way to specify a file system and mount point under it.
Did find 2 how-to guides, neither uses LVM, which means each partition needs to be decrypted with a passphrase - /, /home, swap - that will be 3 entries at every boot.
[http://www.linuxbsdos.com/2014/01/16/manual-full-disk-encryption-setup-guide-for-ubuntu-13-10-linux-mint-16/](http://www.linuxbsdos.com/2014/01/16/manual-full-disk-encryption-setup-guide-for-ubuntu-13-10-linux-mint-16/) - 13.10 guide
[http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04-p4](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04-p4) - 8.04 guide

Just finished reviewing both - they seem to go through the same processes. Moving a backup to a local USB3 disk before trying again.  Think I may have found a way to use LVM (1 passphrase) ... by pausing the installer, fixing the partitions, allowing the installer to continue.  

Only have a few hours to try this today. Should test it inside VMs before attempting it on hardware. That should save lots of time over testing on physical hardware.

---

