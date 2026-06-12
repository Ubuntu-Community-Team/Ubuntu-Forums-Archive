---
title: "Will reinstalling Lucid affect my Windows booting abillity?"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by rodrigo.cr on 2010-05-28
I have Lucid Lynx installed side-by-side with Windows 7. The lucid installation is borked ([http://ubuntuforums.org/showthread.php?t=1484993](http://ubuntuforums.org/showthread.php?t=1484993)), and I figure it's easier and better in the long run to just reinstall it.

However, I do not want to risk leaving my Windows installation unusable.

Is it safe to reinstall just Linux, will this affect my ability to boot windows in any way?

I did a dry run, and got as far as the "install now, delete data on partition", but hesitated as I can't really spare the time to reinstall windows if it becomes screwed up.

---

### Post by garvinrick4 on 2010-05-28
If you run these two pieces of code and copy and paste to this thread we can tell you what your drive looks like and how to install so as not to have what did you say (bork your install). It is actually not to tough of a thing. Also include what type of machine you are using.

```
sudo fdisk -l
``````
sudo blkid
```

---

### Post by rodrigo.cr on 2010-05-28
Using the Ubuntu Live CD (as I can't log in to Lucid) on my **Dell XPS M1530**:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1d65f660

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        9259    74265600    7  HPFS/NTFS
/dev/sda3            9260       19457    81915435    5  Extended
/dev/sda5            9260       19036    78533721   83  Linux
/dev/sda6           19037       19457     3381651   82  Linux swap / Solaris

``````
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="System Reserved" UUID="A2781C7D781C5301" TYPE="ntfs" 
/dev/sda2: UUID="0C24F15124F13DF0" TYPE="ntfs" 
/dev/sda5: UUID="ec3aac71-51e1-4c91-8b35-de703f8a065b" TYPE="ext4" 
/dev/sda6: UUID="ed5f9d17-7921-4eda-bfce-ae9c507cfc96" TYPE="swap" 

```

Thanks!

---

### Post by garvinrick4 on 2010-05-28
Choose manual install.
Your Linux OS is in sda5 so you just make sure you choose sda5 for install of / and on last page you will have an advanced tab in lower right hand corner you choose sda to put your grub in. Always choose sda never anything else not sda1 or sda5 but always sda. 
/ is your root file system (your operating system).  
 Your Partition set-up is a good one so know worries there. Keep your eye open for the
advanced tab. Once you get installed mark this as solved. When you get a chance read up
on Grub2 there are a ton of articles. It is nice to know how to install from Live CD. Will take
any fears away. Have a nice day.

---

### Post by rodrigo.cr on 2010-05-29
> **garvinrick4 said:**
> ...choose sda to put your grub in. 

Thanks for the help. One last question, will the new grub include the option to boot into windows by itself, or will I need to reconfigure it?

Thanks,

Rodrigo

---

### Post by garvinrick4 on 2010-05-29
> **rodrigo.cr said:**
> Thanks for the help. One last question, will the new grub include the option to boot into windows by itself, or will I need to reconfigure it?

Thanks,

Rodrigo
It will give you the option of both installs. Here is nice read on grub.

[http://www.dedoimedo.com/computers/grub-2.html#mozTocId905459](http://www.dedoimedo.com/computers/grub-2.html#mozTocId905459)

---

### Post by rodrigo.cr on 2010-06-01
Worked like a charm, thanks so much. Windows working, Ubuntu rocking, everything's good. Super fast install, too.

---

