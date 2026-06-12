---
title: "No free space on SSD HDD"
date: 2014-07-22
forum: Installation &amp; Upgrades
---

### Post by Bertik on 2014-07-22
Hello all,

I am looking for help, I have installed 14.04 on brand new SSD HDD, I didn't probably looked closely to installation process and now I have a problem.
I did hit "Software Update" and it tells me ***please see in the attached screenshot update.png*** that there is no free space to put updates to.
Disks utility tells me that that's true ***please see in the attached screenshot hdd.png***.

The question is, how can I re-size the partition and to what size? I did use encryption option during OS installation...
Another question, how is this happened? I am 5+ years Ubuntu user and never have had problem like this.

Thanks in advance for the answers,
Regards
Bertik

[ATTACH=CONFIG]254925[/ATTACH][ATTACH=CONFIG]254926[/ATTACH]

---

### Post by Bucky Ball on 2014-07-22
> **Bertik said:**
> ... I didn't probably looked closely to installation process and now I have a problem.

Might have something to do with how it happened, but probably not. I find it is best to choose 'Something Else' and partition manually. Don't like the way Ubuntu creates the partitions 'automagically' in regards to sizes. Can you attach a screenshot of what you have in Gparted. It is hard to diagnose what is happening unless we can see how you currently have the drive partitioned. 

Resizing should be done booting from a LiveDVD/USB, not booted into the hard drive install. You can't resize the OS partition when you're running from it, naturally. ;)

---

### Post by Bertik on 2014-07-22
Forget to attach screenshot...., there now.
Bertik

---

### Post by Bucky Ball on 2014-07-22
That's not saying your ssd is full, it's saying the 240Gb Kingston drive is. At least the details in your first screenshot is. There is no detail about the SSD.

Please open a terminal and issue:

```
sudo blkid
```

Post the output here. Cheers.

---

### Post by Bertik on 2014-07-22
Here it is:

robert@robert-ThinkPad-Edge-E530:~$ sudo blkid
[sudo] password for robert: 
/dev/sda1: UUID="d63284e4-c218-4248-894d-3119f419d537" TYPE="ext2" 
/dev/sda5: UUID="222c48d9-8a7c-469d-9e7f-a191b9403cb3" TYPE="crypto_LUKS" 
/dev/mapper/sda5_crypt: UUID="FIW7nX-UNk7-xHjd-W6Xf-LBC4-Eq3e-szv4CF" TYPE="LVM2_member" 
/dev/mapper/ubuntu--vg-root: UUID="a0ea75dc-a7c8-4694-973e-bc781e9db390" TYPE="ext4" 
robert@robert-ThinkPad-Edge-E530:~$ 

---------------------------

The disk is not full for sure.
There is like 173GB free on the disk... Just the boot partition is 255MB in size and I think the update is trying to use that partition.
[ATTACH=CONFIG]254927[/ATTACH]

Bertik

---

### Post by Bertik on 2014-07-22
Another screenshot from Gparted.

Again, thanks a lot for the help!
[ATTACH=CONFIG]254928[/ATTACH]

---

### Post by Bucky Ball on 2014-07-22
All good. ;) sda5 has an exclamation mark next to it. Right click that entry and select Properties. That might give us a clue about what the problem is. Post it back.

Getting a little confused. You have sda1 (/boot) and sda5 - the encrypted partition with an issue - but also 'Other devices', two block devices. One I'm guessing is a USB dongle, not sure about the other. 

Where do you have Ubuntu installed? On the SSD? That would be where the updates are going. There is no install on sda drive. Presuming once again that the SSD is sdb? Give another Gparted screen shot of sdb by click the drop-down menu in the right corner where /dev/sda is displayed, please.

PS: Have you used encryption previously? I have little to no knowledge of it so perhaps that has something to do with it, but that exclamation mark is not a good sign. :-k

---

### Post by Bertik on 2014-07-22
Here is from Gparted (is it you are asking for?)

[ATTACH=CONFIG]254929[/ATTACH]

---

### Post by Bertik on 2014-07-22
OK, you edited, right? I will do another screenshot for sdb

BTW, sdb is Lenovo installed SSD, I am like 99% sure I did not use it during installation of the OS.

Regards
Bertik

---

### Post by Bucky Ball on 2014-07-22
> Linux Unified Key Setup Encryption is not yet supported.

From the bottom of the last screenshot. This is your first problem. Unless there's a workaround for it, you're going to need to research alternative encryption methods in Linux/Ubuntu and have a re-think. You could try unmounting it (in Gparted), deleting it, and recreating.
> 
BTW, sdb is Lenovo installed SSD, I am like 99% sure I did not use it during installation of the OS.

So how much space is left on the SSD? That must be sdb.

---

### Post by Bertik on 2014-07-22
Here is sdb.
But it has (or it should not to) nothing to do with the OS.
If I remember right, it was unformatable and unusable....
It is just showing there....

sda is the drive where I boot from.

PS: it is first time I used encryption, I needed to to prevent others to looking to other users /home directories.[ATTACH=CONFIG]254930[/ATTACH]

---

### Post by Bertik on 2014-07-22
> **Bucky Ball said:**
> From the bottom of the last screenshot. This is your first problem. Unless there's a workaround for it, you're going to need to research alternative encryption methods in Linux/Ubuntu and have a re-think. You could try unmounting it (in Gparted), deleting it, and recreating.


So how much space is left on the SSD? That must be sdb.

The encryption has been chosen during the installation of the OS, it was given me as a choice... It is build into the Ubuntu.

sda is the main HDD.

sdb - is totaly unusable, I do not see it in the devices at all. It is unformated too... [ATTACH=CONFIG]254931[/ATTACH]

---

### Post by Bucky Ball on 2014-07-22
I can't really help any further as know nothing about encryption and would not have the first clue about finding the details of an encrypted partition regarding how much is used on them. Can't see in Gparted.

What I can say is that sdb2 comes before sdb1, which is odd, and both have exclamation marks next to them. My guess is same error as sda as outlined in my last post. Again, this could be normal for an encrypted partition, I wouldn't know, sorry. 

Another thing I can say is that with an install on a 6Gb or 8Gb partition, yes, it could very well be no space left if that's where your updates are going.

PS: I think you can encrypt single folders. Perhaps that would be preferable to the whole drive. At least get you running. You are obviously booting fine from sda with this machine?

Just a note: Generally, the operating system would be running on the SSD. This is the way it's done because of the SSD's superior speed. Rule of thumb is normally OS on the SSD and data on the HDD. Any reason for going the other way? Your experience would be vastly improved by reversing the order. ;)

---

### Post by Bertik on 2014-07-22
Thanks a lot Bucky Ball for all your help.
Not solved, but a do appreciate your time, though.

PS: It is all SSD, no regular spinning HDD in my system :) (I did mention : sda is the main HDD (my mistake, I meant SSD))

Regards
Bertik

---

### Post by Bucky Ball on 2014-07-22
> **Bertik said:**
> 

PS: It is all SSD, no regular spinning HDD in my system :) (I did mention : sda is the main HDD (my mistake, I meant SSD))


Ah, now I'm with you. Try this in a terminal:

```
sudo fdisk -l
```

Post the output.

---

### Post by oldfred on 2014-07-22
I do not know encryption nor LVM. But encryption uses LVM.

 And gparted does not see nor work with LVM partitions, you have to use LVM tools and you have to unencrypt before you can do anything. As the purpose of encryption is to prevent any tool from modifying or reading your system. So that gparted shows errors is normal with encryption.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by Bucky Ball on 2014-07-22
> **oldfred said:**
> ... gparted shows errors is normal with encryption.

       

Learn something everyday. Had my suspicions. Thanks, oldfred. ;)

---

### Post by oldfred on 2014-07-23
Looks like it may be a bug somewhere. 
Another user with exactly the same error message also using encryption with LVM.

[http://ubuntuforums.org/showthread.php?t=2235403](http://ubuntuforums.org/showthread.php?t=2235403)

---

### Post by Bertik on 2014-07-24
Hello Bucky Ball,

before I do paste here 
```
sudo fdisk -l
```
I have to mention weird thing.
I did log of from my user account and loged in to another (admin also) and run the update. All went just fine $&$*#^@&**(. Go figure. Might be that the partition was somehow locked....

So, I will mark this thread as SOLVED.

Here is the output from fdisk, just for the reference
```
Disk /dev/sda: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007e8e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   468860927   234179585    5  Extended
/dev/sda5          501760   468860927   234179584   83  Linux

Disk /dev/sdb: 16.0 GB, 16013942784 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31277232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8c47d156

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1        14497792    31275007     8388608   84  OS/2 hidden C: drive
/dev/sdb2            2048    14495743     7246848   73  Unknown

Partition table entries are not in disk order

Disk /dev/mapper/sda5_crypt: 239.8 GB, 239797796864 bytes
255 heads, 63 sectors/track, 29153 cylinders, total 468355072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 231.6 GB, 231630438400 bytes
255 heads, 63 sectors/track, 28160 cylinders, total 452403200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 8166 MB, 8166309888 bytes
255 heads, 63 sectors/track, 992 cylinders, total 15949824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

```

Thank you very much for all the help, regards
Bertik

---

### Post by Bucky Ball on 2014-07-24
Great news! No problems. Enjoy. ;)

---

### Post by Bochigger on 2015-03-10
For others searching to a solution to this issue (update install fails due to full /boot on encrypted Ubuntu 14.04 64bit), you can try this, which worked for me:

apt-get autoremove

It cleared out obsolete files in the /boot partition.

---

