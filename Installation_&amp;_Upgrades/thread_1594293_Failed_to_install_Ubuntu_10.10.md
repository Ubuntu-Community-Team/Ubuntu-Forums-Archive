---
title: "Failed to install Ubuntu 10.10"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by olddai on 2010-10-12
I downloaded and burned the iso at 12x speed and configured the BIOS so that the computer would boot from a CD. I ran the Live CD and everything seemed to be fine until i was informed that the installation had failed because of problems with my hard drive. But worst was to come when i reconfigured the BIOS so as to boot from the hard drive and all i got was a completely blank screen. I don't have a Ubuntu 10.04 Live cd handy so i have to use a different distro's live cd just to get on line. Would really appreciate any help. Thanks

---

### Post by olddai on 2010-10-12
I can run the Ubuntu 10.10 "Live CD" but cannot install Ubuntu 10.10. I opened a terminal and typed: update-manager -d and was informed that the system is upto date. Would settle for Ubuntu 10.04 but when i reboot the computer the screen remains comletely blank? Help anyone please.

---

### Post by olddai on 2010-10-12
Thought i'd have an at least one reply? Thanks for nothing!

---

### Post by DougieFresh4U on 2010-10-12
> **olddai said:**
> Thought i'd have an at least one reply? Thanks for nothing!

YIKES!!
Be patient.
You have not given any info as to what machine you are using or any of the hardware??

---

### Post by Rubi1200 on 2010-10-12
Use the LiveCD and post the results of the boot-script linked at the bottom of my post.

Thanks.

---

### Post by olddai on 2010-10-12
Sorry for being so impatient. Just hope you'll put it down to my age.

I have done exactly as Rubi1200 said and the result is below.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   303,368,191   303,366,144  83 Linux
/dev/sda2         303,370,238   312,580,095     9,209,858   5 Extended
/dev/sda5         303,370,240   312,580,095     9,209,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        f600536c-89e0-4b53-9e38-62836710f901   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        4be7c089-47b0-4145-be6c-048e63d10228   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f600536c-89e0-4b53-9e38-62836710f901 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4be7c089-47b0-4145-be6c-048e63d10228 none            swap    sw              0       0

---

### Post by Rubi1200 on 2010-10-12
The most obvious problem is that GRUB has not been installed/installed properly.

You need to follow the instructions in this guide:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Let me know if this is clear and/or you need additional help.

---

### Post by olddai on 2010-10-12
Hello Rubi1200

I think i can follow the tutorial but coupd you make clear something for me first>


[COLOR=Red]**Important:**[/COLOR] All instances of **[COLOR=DarkRed]sdX[/COLOR]** and **[COLOR=DarkRed]sdXY[/COLOR]** must be replaced with the correct drive/partition for your system. (sda, sdb, sda1, sda5, sdb5, etc). **[COLOR=DarkRed]X[/COLOR]** is the drive letter. **[COLOR=DarkRed]Y[/COLOR]** is the partition number. The first drive is "a" and the first partition is "1". Example: sd*a1*


**[COLOR=Navy]1. Chroot into your real system.[/COLOR]** The  following set of commands will mount the necessary system files to allow  the chroot and place you in a terminal where the commands will work on  your real installation. 

Change [COLOR=DarkRed]sd**XY**[/COLOR] to correct value (for example, sda5, sdb1, etc.).
     Code:
     sudo mkdir /mnt/temp  sudo mount /dev/[COLOR=DarkRed]**sdXY**[/COLOR] /mnt/temp  # Example:  sudo mount/dev/sd**a5**  /mnt/temp for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done sudo chroot /mnt/temp 

 would the sdXY correct value in my case be sda1?

Thanks

---

### Post by Rubi1200 on 2010-10-12
Correct; sda1 is the partition where you have Ubuntu installed.

Therefore, the GRUB files need to be reinstalled there.

The methods suggested in the guide to try first are usually the best way to do things. However, since your installation is missing the GRUB files, the chroot method should be the best thing to do.

Good luck and if you get stuck or are unsure, ask please.

---

### Post by olddai on 2010-10-12
Shall attempt to carry out the instructions. Fingers crossed everything will work out.

---

### Post by zuerston on 2010-10-12
> **olddai said:**
> Shall attempt to carry out the instructions. Fingers crossed everything will work out.



Well WHATS UP DOC? ehhhh we wanna know!
is it woikin?
:confused:

---

### Post by standingfire on 2010-10-12
Can you see anything, like the old hard drive with the live CD, is there a possibility that you created an LVM partition when you made your initial installation ?

---

### Post by olddai on 2010-10-12
Hi Rubi1200

Following on from your last post i started by copying and pasting the following into a terminal

```

sudo mkdir /mnt/temp  sudo mount /dev/[COLOR=DarkRed]**sda1**[/COLOR] /mnt/temp  # Example:  sudo mount/dev/sd**a5**  /mnt/temp for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done sudo chroot /mnt/temp
```and this was the result

```

ubuntu@ubuntu:~$ sudo mkdir /mnt/temp 
mkdir: cannot create directory `/mnt/temp': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp  # Example:  sudo mount/dev/sda5  /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
ubuntu@ubuntu:~$ sudo chroot /mnt/tempexit

```Think this is all way above me

---

### Post by Rubi1200 on 2010-10-12
Try running the commands like this (copy and paste to avoid mistakes)

```
sudo mkdir /mnt/temp
```
```
sudo mount /dev/sda1 /mnt/temp
```
```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
```
```
sudo chroot /mnt/temp
```
See if this brings you to the root prompt mentioned in the guide.

If not, we will have to try something else.

Let me know how it goes.

---

### Post by punkybouy on 2010-10-12
I always thought GRUB was part of the last bit of the installation.  If GRUB did not install the installation may be lacking more than just the boot loader.  Did you run a chksum on the downloaded iso?  I have always used the alternate CD to do installations as it has the option of encrypting the drive.

---

### Post by olddai on 2010-10-13
Hi Rubi1200

I typed in the commands you posted and got this response:
root@ubuntu:/#

I then went back to the guide and typed in the following:
apt-get update #***

and got this response:
root@ubuntu:/# apt-get update   # ***
E: List directory /var/lib/apt/lists/partial is missing. - Acquire (2: No such file or directory)
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
root@ubuntu:/#

---

### Post by Rubi1200 on 2010-10-13
Do you have internet connectivity from the LiveCD?

EDIT: from that root prompt; run just this ```
apt-get update
``` and nothing else. If there are errors report back please.

---

### Post by olddai on 2010-10-13
Have done as you said and got the following result:

ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# apt-get update
E: List directory /var/lib/apt/lists/partial is missing. - Acquire (2: No such file or directory)
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
root@ubuntu:/#

---

### Post by olddai on 2010-10-13
Yes i am able to get online via the Live CD

---

### Post by shuituzi on 2010-10-13
I downloaded and burned the iso at 12x speed and configured the BIOS so that the computer would boot from a CD. I ran the Live CD and everything seemed to be fine until i was informed that the installation had failed because of problems with my hard drive. But worst was to come when i reconfigured the BIOS so as to boot from the hard drive and all i got was a completely blank screen. I don't have a Ubuntu 10.04 Live cd handy so i have to use a different distro's live cd just to get on line. Would really appreciate any help.
[]("http://www.louboutincook.com/")

---

### Post by Rubi1200 on 2010-10-13
> **olddai said:**
> Have done as you said and got the following result:

ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# apt-get update
E: List directory /var/lib/apt/lists/partial is missing. - Acquire (2: No such file or directory)
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
root@ubuntu:/#

Ok, we can try the following from the same root prompt. But, if this does not work it might be easier and less painful just to do a reinstall of the whole system again.

Run the commands in order and report errors, if any:

```
apt-get autoclean

apt-get clean

apt-get update

apt-get upgrade

apt-get dist-upgrade

apt-get -f install

dpkg --configure -a
```

If all this goes to plan, then continue with the instructions from the first guide to reinstall GRUB.

---

### Post by olddai on 2010-10-13
Hi Rubi1200

Bad news i'm afraid. 

ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (2: No such file or directory)
E: Unable to lock the download directory
root@ubuntu:/# apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (2: No such file or directory)
E: Unable to lock the download directory
root@ubuntu:/# apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (2: No such file or directory)
E: Unable to lock the download directory
root@ubuntu:/# apt-get update
E: List directory /var/lib/apt/lists/partial is missing. - Acquire (2: No such file or directory)
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
root@ubuntu:/# apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
root@ubuntu:/# 
root@ubuntu:/# apt-get dist-upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
root@ubuntu:/# apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
root@ubuntu:/# dpkg --configure -a
dpkg: unable to access dpkg status area: No such file or directory
root@ubuntu:/#

---

### Post by Rubi1200 on 2010-10-13
Hi olddai,
I am sorry, but I have run out of ideas. The errors suggest an installation gone badly wrong.
> No such file or directory

I would suggest you do a fresh install and start from the beginning again.

Download the .iso again and check the MD5SUM before burning to CD at the lowest possible speed.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Of course, someone else may come along with other ideas, in which case you may want to wait for input from other users. But, if it was me, I would go for a clean install.

---

### Post by olddai on 2010-10-13
Hi Rubi1200

During the last attempt to install Ubuntu 10.10 i got as far as i was just waiting for the install to finish before things started to go wrong. I shall download Ubuntu 10.10 once again and as advised i will burn the ISO image at the slowest speed and hope that will be alright.

Many thanks for all the help!

---

### Post by Rubi1200 on 2010-10-13
You are more than welcome :)

If you need additional help either post again in this thread or start a new one.

Good luck!

---

### Post by punkybouy on 2010-10-16
Any updates?  So what happened?

---

