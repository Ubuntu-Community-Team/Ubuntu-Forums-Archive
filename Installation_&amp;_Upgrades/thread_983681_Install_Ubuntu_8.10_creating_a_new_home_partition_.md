---
title: "Install Ubuntu 8.10 creating a new /home partition while dual-booting with Windows XP"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by Dave54 on 2008-11-15
I have a blank 250GB hard drive. I installed Windows XP, telling it to use 126GB. I plan to install Ubuntu into the other 124GB. The last time I did this, GRUB became my new boot loader and allowed me to select either Windows XP or Ubuntu.

This time, I wanted to install Ubuntu 8.10 with a separate /home partition. I booted the CD, clicked the Install icon, and when the time came for partitioning the hard drive, I selected Manual. I had no idea what to do here, so I did a bunch of research. This is what I found:

1. A hard drive can have a maximum of four primary partitions, or a maximum of three primary partitions and one extended partition.
2. A hard drive can only have one extended partition.
3. An extended partition does not itself hold data. Instead, an extended partition is split up into any number of logical drives that essentially function as primary partitions.
4. A DOS operating system can not boot from a logical drive, but all other operating systems can.
5. It is recommended to have a SWAP partition of about twice your RAM, especially if you would like to hibernate.

Having learned this information, I went back to the manual partitioning dialogue. Windows was using one partition, and I wanted to make three more (/, /home, and SWAP), so I could make them all primary partitions.

Here's the partitions I made, in order:
sda2 Primary Type:SWAP Size:4GB
sda3 Primary Type:ext3 Size:20GB  Mount-point:/
sda4 Primary Type:ext3 Size:100GB Mount-point:/home

With that, I finished the installation. When I reboot, I go straight into Windows XP. GRUB never says it is loading, so I imagine GRUB was not installed as my boot loader.

Where did I go wrong?

Dave

---

### Post by taurus on 2008-11-15
Now that you have installed Ubuntu on your harddrive, I guess all you need is to install GRUB to MBR then.  Maybe this guide helps.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Dave54 on 2008-11-15
> **taurus said:**
> Now that you have installed Ubuntu on your harddrive, I guess all you need is to install GRUB to MBR then.  Maybe this guide helps.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Thank you for the guide. I will start following it, but I am also open to the possibility of reinstalling Ubuntu. (Seriously, it takes less than 10 minutes)

I'll report back when I finish the guide.
Dave

---

### Post by Dave54 on 2008-11-16
Ok, things have gotten a little messier.

To make things simpler, I did not mention that I have three hard drives in my computer. However, it seems important to say now, because some of the numbers are different due to that fact.

I followed the tutorial which had me boot the CD, open terminal, and enter "sudo grub". Then I entered the following:```
grub> find /boot/grub/stage1
 (hd2,2)

grub> root (hd2,2)

grub> setup (hd2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd2) (hd2)1+16 p (hd2,2)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub> quit
```All seems well so far. So I reboot, GRUB starts, I select Windows, and get the following error:```
error 13: invalid or unsupported executable format
Press any key to continue.
```So I boot into Ubuntu (which works), open terminal, and enter "gksu gedit /boot/grub/menu.lst". At the very bottom of my menu.lst is the following:```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```Is there anything wrong with this?
That is my main question, but what follows are a few other curious problems.
When I exit gedit, my terminal says this:```
dave@Dave-PC:~$ gksu gedit /boot/grub/menu.lst 
I/O error : No such file or directory
I/O error : No such file or directory
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSdave@Dave-PC:~$ 
```Yes, the "dave@Dave-PC:~$" part was floating in the middle of the line, right after the S's.
I start to think that an update might solve my problem. I install all the updates (including a kernel update), but it doesn't change my GRUB problem. From the GRUB menu, there is still only one kernel version: 2.6.27-7-generic. Is this the most recent? Why doesn't the old one show? Is Ubuntu updating my menu.lst like it should? How would I know?

I'm also worried that ubuntu is feeling extremely buggy: When I click, there's a delay before it detects it. Ubuntu randomly does not detect when I take my finger off the mouse button, so it thinks I'm still holding it down. I decided to enable the restricted nvidia drivers so that I could enable desktop effects. A window came up saying "searching for compatible drivers, 0%", and it stayed at 0% until the driver was completely downloaded and installed. I rebooted as it said I should and enabled desktop effects only to find more bugs: The title bar on windows become glitched after the mouse passes over it. (Grey stripes appear on it and the buttons float off the bar.) The Hardware drivers dialogue displays the three restricted drivers each three times in three columns (that dialogue is not supposed to have more than one column).

I wonder if my install is corrupted or if I'm just that unlucky?

---

### Post by taurus on 2008-11-16
So right now, Ubuntu boots but windows won't.  Can you post the layout of your disk?

```
sudo fdisk -l
```

---

### Post by Dave54 on 2008-11-16
> **taurus said:**
> So right now, Ubuntu boots but windows won't.  Can you post the layout of your disk?

```
sudo fdisk -l
```
That is correct.
Here it is:```
dave@Dave-PC:~$ sudo fdisk -l
[sudo] password for dave: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000e45b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x257fc65d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121601   976760001   83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005e3f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       15200   122093968+   7  HPFS/NTFS
/dev/sdc2           15201       15686     3903795   82  Linux swap / Solaris
/dev/sdc3           15687       18118    19535040   83  Linux
/dev/sdc4           18119       30401    98663197+  83  Linux
dave@Dave-PC:~$ 
```Everything looks correct to me:
sda1 and sdb1 are just data storage.
sdc1 is windows XP
sdc2 is Linux swap
sdc3 is the root file system (/)
sdc4 is /home

---

### Post by taurus on 2008-11-16
Can you edit /boot/grub/menu.lst and place a # in front of these lines?

```

[COLOR="Blue"]#[/COLOR]title		Microsoft Windows XP Professional
[COLOR="Blue"]#[/COLOR]root		(hd2,0)
[COLOR="Blue"]#[/COLOR]savedefault
[COLOR="Blue"]#[/COLOR]makeactive
[COLOR="Blue"]#[/COLOR]map		(hd0) (hd2)
[COLOR="Blue"]#[/COLOR]map		(hd2) (hd0)
[COLOR="Blue"]#[/COLOR]chainloader	+1

```
Then, add these lines directly below it.

```

title Windows XP
rootnoverify (hd2,0)
makeactive
chainloader +1

```
Save it and reboot.  Now, see if you can boot your windows.

---

### Post by Dave54 on 2008-11-16
I did what you said. The end of my menu.lst now looks like this:```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
#title		Microsoft Windows XP Professional
#root		(hd2,0)
#savedefault
#makeactive
#map		(hd0) (hd2)
#map		(hd2) (hd0)
#chainloader	+1

title Windows XP
rootnoverify (hd2,0)
makeactive
chainloader +1
```I restarted, selected Windows, and got the same error:```
error 13: invalid or unsupported executable format
Press any key to continue.
```

---

### Post by Dave54 on 2008-11-16
My 250 GB drive is PATA, but my 500 GB and 1 TB drives are SATA. Also, one is connected to some annoying JMicron thing and the other isn't. My point is, what if my computer is terrible at ordering my drives? GRUB when it's booting could have a different order than when after Ubuntu has booted.

I'm looking for a grub command that displays connected hard drives, but I can't find one.

---

### Post by Dave54 on 2008-11-16
At boot, when GRUB came up, I hit Esc to stop the countdown. Then I hit "C" to enter the grub command-line. Then I typed "root (" and hit tab to see the auto-complete possibilities. After working around with that a little, I was able to gather the following information:```
(hd0,0) filesystem type unknown, partition type 0x7
(hd0,1) filesystem type unknown, partition type 0x82
(hd0,2) filesystem type is ext2fs, partition type 0x83
(hd0,3) filesystem type is ext2fs, partition type 0x83

(hd1,0)

(hd2,0)
```So it would seem that sdc is (hd0). I'm now editing my menu.lst to the following:```
title Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1
```I'm assuming the partitions should still be in order. I'll tell you how it turns out.

---

### Post by Dave54 on 2008-11-16
It worked! I can boot windows again!

Look back at post #4. From the live CD, I run:```
grub> find /boot/grub/stage1
 (hd2,2)
```So I guess grub from the live CD felt that sdc was (hd2), and meanwhile grub from boot felt that sdc was (hd0). Does this explain what I originally found in my menu.list?```
root		(hd2,0)
map		(hd0) (hd2)
map		(hd2) (hd0)
```What would have been the correct menu.lst entry?

---

### Post by Dave54 on 2008-11-16
I'm not marking this thread as solved yet, as my main question is still unanswered:
How do you install Ubuntu 8.10 creating a new /home partition while dual-booting with Windows XP?

Now that I know how to repair grub, tomorrow I will reinstall Ubuntu a bunch of times. I want to know, if I install Ubuntu and let it do the partitioning, will the grub be written as it is supposed to? Actually, I think the installer is so limited, that would be impossible unless I remove my SATA hard drives. (It feels it can get more space by sizing down one of my other partitions, so it won't even consider creating a partition in the unpartitioned space.) If I remove my other hard drives and use the same manual procedure I used before, will it work then? What if I use all logical drives?

I will post back when I get the answers. Thanks for the help, taurus.

Dave

---

### Post by RealG187 on 2008-11-16
You can mount /home to a different partition?

---

### Post by Dave54 on 2008-11-16
> **RealG187 said:**
> You can mount /home to a different partition?

Yes, you can. Here's the general idea:

1. You install Ubuntu, creating two partitions: a small one (about 10 GB) where Ubuntu is installed (/) and a large one that uses up the rest of the drive, and is mounted to /home.

2. As you use Ubuntu, all your documents, music, and preferences are kept in the /home partition.

3. The next version of Ubuntu comes out.

4. Instead of upgrading (which can cause problems) you reformat the Ubuntu partition and install Ubuntu fresh. Then you mount the /home partition, and you have all your documents, music, and preferences without having to go through a long backup procedure.


Having a separate /home partition helps not only in upgrading, but in emergency situations too. Let's say you accidentally remove some system files and can't boot. Or you corrupt your file system. In either case you can reinstall without worry of losing your documents.

Everywhere I go I see people recommending having a separate /home partition. Sadly, this configuration is not automatically supported by Ubuntu. I have seen quite a few bug reports about the fact that this is not an option in the Ubuntu installer.

---

