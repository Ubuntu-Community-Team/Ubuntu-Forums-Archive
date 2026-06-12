---
title: "Possible To Install Ubuntu 10.04 on RAID 0?"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by hayhursm on 2010-07-01
I'm writing this to vent, so forgive me if I come across as rude but I  have wasted half my weekend trying to figure this out. I have come to  the conclusion that it would be easier to pick fly droppings out of the  carpet with boxing gloves on rather than install Ubuntu on a RAID 0  setup.  Why is this so difficult?  First, I tried installing Ubuntu  10.04 and got the ext4 file system error during the installation  process.  I tried partitioning the two RAID 0 HDD's with GParted in  10.04 but it would not recognize my RAID 0 setup as it only listed the  HDD's individually.  So then I tried GParted in 9.10 and to my surprise  it recognized my RAID 0 setup.  After a little trial and error I finally  got passed the ext4 file system error.  But my excitement quickly died  as I was about 95% complete on the installation process and then a GRUB  error popped up.  After trial and error and reading some complicated  tutorials for a novice Linux user I finally got the installation to  finish in 9.10.  Why did an older stable release of Ubuntu successful  install over a new one?  Does anyone know why GParted in 10.04 would not  detect the RAID 0 but GParted in 9.10 did?  Seems like the developers  might have went backwards on this one.

Thanks for the help!

---

### Post by ronparent on 2010-07-01
I can't answer all of your questions, but, I can verify that your observation are correct. The main thing is that. yes, you can install 10.04 to a raid as well as boot from the raid. To save myself some repeating, here are some observations and instructions I provided someone else:

> Each Ubuntu release has had it own quirks with regards to installing on a raid. The 10.04 desktop release does come with dmraid which allows you to access your raid (apparently '/dev/mapper/isw_chibcceegh_Volume0'). The quirks are 1)that gparted run from 10.04 will not work on a raid partition and the partitioning step of the installation will fail 2) that the installer will try to install the grub boot loader to /dev/sda and that if this is one of your raid drives, that will fail.

The workarounds I have used are to:

1) pre-format (ext2, ext3 or ext4, it doesn't matter) the target partition with an earlier version of Ubuntu, either installed or live cd. The catch is that you must have dmraid installed or install it. This can be done to a live cd session if you have internet capability - gparted will not see the raid or its partitions unless the raid drives are activated by dmraid.

To install dmraid in a terminal - Code:

Quote:
sudo apt-get install dmraid
To activate the raid - Code:

Quote:
sudo dmraid -ay
You now can start gparted (System>Administration>Gparted or Partition Disks depending on the version your running from) and select an unallocated space to create your target sized as you want it - or resize an existing partition to give you unallocated space in which to create your partition in. You will also have to create a swap partition if there is not already one present. We probably don't have to address it here, but if you already have two or more partitions on this array, you should create additional partitions in an extended partition (you are currently limited to four total primary partitions including an extended partition on any drive). Note the name of this partition. Once your pre-formated partitions is created on the raid you can boot into your 10.04 live cd. 

At this point you pick the desktop icon to start the installation of 10.04. When you reach step 4 of 7 you will pick the option to manually specify the partition you have previously formatted to install to. When step 5 of 8 appears, select your partition and click 'change' at the bottom of the window. In the box select the format from the drop box choices (probably ext3 or ext4, same as what you previously formated). Do NOT check to format. In the next drop down select '/' - the mount point you file system is to be installed to.

2) To hopefully handle the 2nd quirk, at step 8 of 8 you will click on the box labeled 'Advanced'. At this point you should be able to select the top array name (the name representing the entire array, not one of the partitions) from a drop box. After this you have done everything you can do. You can click next and you system will be setup on the chosen partition. I have just run into the problem in Mint where this was not adequate. The installer still tried to install to sda and resulted in a 'fatal failure'. If this happens don't despair - it can still be fixed. Just continue to install without the boot loader. I will have to research the specific steps and get back to you on this if we have to address it.

As you can tell, raid in Ubuntu is not for the faint hearted or under informed. It is doable. You will have to do some learning along the way. If you are going to try and stick with it, I or others will be able to help along the way.
__________________

---

### Post by hayhursm on 2010-07-01
> **ronparent said:**
> I can't answer all of your questions, but, I can verify that your observation are correct. The main thing is that. yes, you can install 10.04 to a raid as well as boot from the raid. To save myself some repeating, here are some observations and instructions I provided someone else:


__________________


Thank you for the help, I guess we can just hope this will be corrected in future releases to prevent all the headaches.

---

### Post by ronparent on 2010-07-01
Amen to that - I've been waiting a while but I'm not holding my breath.

---

### Post by gator on 2010-07-02
use the alternate install cd for raid and lvm - works perfectly

---

