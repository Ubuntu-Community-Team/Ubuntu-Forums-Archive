---
title: "Hard Disk Partitions not detected in Ubuntu 10.10 installation from LiveCD"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by jinjanjaa on 2010-11-21
Hello every1,
I tried to install **ubuntu 10.10** today through **livecd**. but the partitions in my **60gb samsung harddisk** are not detected. **my entire harddisk is shown as unallocated free space**. also gparted is not detecting the partitions as well. i am currently not facing any problems with my partitions in windows xp.

i tried the solution given here (to no avail):
[http://ubuntuforums.org/showthread.php?t=1510017](http://ubuntuforums.org/showthread.php?t=1510017)

**I have had no such problems with previous versions of ubuntu. **

---

### Post by srs5694 on 2010-11-21
First, unless you're *sure* that the *cause* of the problem is the same, you should *never* blindly apply a procedure posted to solve one person's problem to your own computer. It's unlikely that you did any damage to your system in this specific case, but the procedures you see posted here (or on other forums for Ubuntu, other Linux distributions, or even OS X or Windows) are often designed to do specific things to help solve very specific problems. Those same procedures can actually do more harm than good when applied inappropriately, even if the initial symptoms seem similar. People who blindly apply such procedures frequently just dig themselves in deeper, sometimes losing important data as a result.

Now, to your specific problem, you'll have to provide us with more details. Boot the installer into live CD mode, or boot any Linux rescue CD, and type the following command:

```

sudo fdisk -lu

```

Note that's a lowercase "L" in "-lu", not a digit 1. Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility. This command will provide us with information necessary to diagnosing the problem.

In my experience, there's about a 50/50 chance that the problem is as described [on this Web page of mine,](http://www.rodsbooks.com/missing-parts/index.html) so you might want to check that page; but please *don't* follow the procedure described there for resolving the problem unless you're sure the cause is the same one described on the page!

---

### Post by jinjanjaa on 2010-11-21
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 60.1 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders, total 117304992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3f3a3f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20964824    10482381    7  HPFS/NTFS
/dev/sda2        20964825   117290564    48162870    5  Extended
/dev/sda3        69127695   117290564    24081435    7  HPFS/NTFS
/dev/sda5        20964951    69127694    24081372    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by jinjanjaa on 2010-11-21
Also i tried booting and installing from an ubuntu 9.10 livecd. Even that dint recognise my partitions.

---

### Post by marc118118 on 2010-11-21
I am having a very similar problem.

Trying to install Ubuntu 10.10 on a Advent 5771 currently running vista. I run the live cd from powering on and get as far as the partition manager, then no matter which method of configuration I choose, the installation always fails as the partitions cannot be formatted. The installation then hangs requiring a hard shut down.

The machine then boots back into vista absolutely fine despite the failed ubuntu 10.10 even though supposedly it had rewritten the partition table.

I have also tried to run ubuntu 9.4 from the live cd, which worked perfect on numerous times in the past, and even the gnome partition manager on 9.4 cannot instal for the same hhd / partition reasons.

I have even formatted the entire hard disk and zero filled it, attempted to install Ubuntu on the entire hdd and it still never gets past the partition manager again.

Any advice? Could this be a hardware issue with the drive that windows is either able to mask or ignore and ubuntu can't ??    :P

---

### Post by srs5694 on 2010-11-21
jinjanjaa,

First, please post output such as that from fdisk between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags, as I instructed; that makes it much more legible, since it preserves the formatting inherent in the original monospaced output. Cutting and pasting without formatting it in this way results in the forum software removing "extra" spaces, which destroys the column associations of the original output.

Second, you've got a badly corrupted partition table; something has either either converted your current /dev/sda5 from a primary partition into a logical partition or it's extended the /dev/sda2 logical partition to cover /dev/sda3. I'm also concerned about the "omitting empty partition (5)" message that fdisk produced. It could be there's a small partition that's gotten lost.

I can think of several ways to proceed, but it would be helpful to know what each of those partitions is. Presumably this is a Windows boot disk, but it's not clear what each of those partitions is. Also, which partition(s) do you intend to resize to make room for Linux? If you can completely delete a partition, it might simplify recovery. If Windows sees anything more than three NTFS partitions, you should not try anything more until you've figured out what Windows is seeing, since you might destroy a partition that even fdisk isn't seeing. Please post back with those details.

marc118118,

Please start a new thread. In my experience, attempting to address two peoples' problems in a single thread gets very confusing very fast. Please try to provide more specific information in your new thread, including the "fdisk -lu" output I asked of jinjanjaa, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility.

---

### Post by jinjanjaa on 2010-11-22
srs5694,

i'll post the info u need shortly. meanwhile please tell me if there is a software that can be used in windows xp to fix the errors (or watever) in my partition table??
a one shot comprehensive solution??

---

### Post by jinjanjaa on 2010-11-22
[IMG]http://img34.imageshack.us/img34/7446/picfo.png[/IMG]

My partition details from windows perspective....

let me refer to the dives with volume labels. the "Just 4 Ubuntu" dive is what i cleared up for ubuntu. "Windows XP" partition holds XP. and the storage space has some multimedia and other content that i can clear up, if needed. 

MOST IMPORTANTLY, i see a new unallocated free space there (of 22.97 GB) which does not exist at all!!!!  my hd is only 60gb which is distributed completely between the three existing partitions.

hav i furnished enuf details??

---

### Post by wkavinsky on 2010-11-22
First of, if you can shift the data on your media partition to an external HDD for backing up, it might be an idea to do that before you do anything else.

Also, do you have access to the windows recovery console / a genuine XP boot disk?

---

### Post by wilee-nilee on 2010-11-22
> **wkavinsky said:**
> First of, if you can shift the data on your media partition to an external HDD for backing up, it might be an idea to do that before you do anything else.

Also, do you have access to the windows recovery console / a genuine XP boot disk?

[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

---

### Post by jinjanjaa on 2010-11-22
@ wilee-nilee
i am not trying to remove linux. i am trying to install it.

@ wkavinsky  
thx 4 the tip.i was going to do it anyway. but r u suggesting a complete format and install?? and yes i have access to win xp recovery console

---

### Post by wilee-nilee on 2010-11-22
n

---

### Post by srs5694 on 2010-11-22
It appears that the solution to your problem is easy: Using fdisk, delete /dev/sda3. (Precise instructions are below.) This partition appears to be the "Just 4 Ubuntu" partition from your screen shot. (I say this because the "Just 4 Ubuntu" partition appears to be a primary partition of the same size as the /dev/sda3 primary partition. Linux's /dev/sda5 is roughly the same size, but it's a logical partition, which seems to match your "Storage Space" Windows partition.) Once /dev/sda3 is deleted, the Ubuntu installer should be able to see the other partitions and it should be able to create partitions itself in the free space within the extended partition. For added safety, I suggest you verify the identity of the /dev/sda3 partition by mounting it to be sure it holds no files. I'm not sure if the Ubuntu live CD mounts such partitions by default, though. If it doesn't, you'll need to type "sudo mount /dev/sda3 /mnt", whereupon you can type "ls /mnt" to check if there are any files on the partition. If there are no files, unmount the partition with "sudo umount /dev/sda3" and proceed with deleting the partition:


[list=1]
[*]Type "sudo fdisk /dev/sda".
[*]Type "p" to view the partition table  to be sure you're working on the right disk; if not, type "q" to quit.
[*]Type "d" to delete a  partition. You'll be prompted for a number; type "3".
[*]Type "p" to view the new table and verify that it's correct. If something looks strange, type "q" to quit without saving and post details back here.
[*]If all seems well, type "w" to write your changes to disk.
[/list]


You should now be able to reboot and proceed with Linux installation. When you get to the partitioning screen, tell it you want to manually partition. Create a swap partition of 1-2 times your RAM size and give the rest to a root (/) partition. If you're asked, tell it to make both of these logical partitions rather than primary partitions. (Ordinarily, I recommend creating a separate /home partition, too, but you'll have so little disk space for Linux that this isn't advisable, IMHO.)

Instead of manually partitioning, there are other options. If there's one to use all the existing free space, you could use it, but I don't recall offhand if such an option exists with Ubuntu. *Do not* select the option to use all the disk space (not just all the *free* disk space), since that'll wipe out everything you've got on the disk. I know there's an option to install side-by-side with Windows, but that's likely to adjust your partition sizes, so I don't recommend using that option.

---

### Post by srs5694 on 2010-11-22
> **wilee-nilee said:**
> Boot the live cd of Ubuntu from a cd or thumb drive. go to gparted take a screen shot of that. The information that we have so far is conflicted, and it is apparent that you are a new user.

GParted will just show an empty disk, just like the installer did. They're both based on libparted, and they tend to flake out in the same way with corrupt partition tables. Jinjanjaa has already posted the output of "fdisk -lu", which is much more reliable with a corrupt partition table.

Gory technical details:

Something (I'm guessing whatever Windows software jinjanjaa used to set up the partition for Ubuntu) goofed badly; it sized the new Ubuntu partition correctly, but instead of entering it into the partition table as a logical partition, it created it as a primary partition. The result is that the /dev/sda3 partition (which jinjanjaa intended for Ubuntu) overlaps with /dev/sda2 (the existing extended partition). That's why Windows is reporting the free space that doesn't exist; its partitioner hasn't noticed that some space is allocated twice, and is just reporting what's been allocated to primary or extended partitions. Tools based on libparted, by contrast, report this type of error as a completely empty disk. Linux's fdisk shows the actual partition table entries, enabling diagnosis (and repair, since fdisk will operate on such disks).

---

### Post by wilee-nilee on 2010-11-22
Your preaching to the choir man I know whats going on there,;) Carry on I don't have the energy to do this.

---

### Post by jinjanjaa on 2010-11-22
thx a lot for your how-to srs5694 but i dint use it.

i solved the prob by downloading Partition Magic software. it fixed overlapping partitions error in partition table. now gparted and ubuntu install is able to detect my partitions. i formatted both my logical partitions and now installing ubuntu. i am posting this reply from the livecd with the installation going on in the background.

will tell u all about what happened after install tomorrow.

thx 4 every1 who replied. 

@wilee-nilee
i might not hav knowledge on certain areas. but i am no inexperienced ubuntu user. ive faced a lot of problems using ubuntu and hav written a lot of how-tos on solving them. many hav followed my how-tos with success. fyi, even this is going to become a how-to.

---

### Post by wilee-nilee on 2010-11-22
> **jinjanjaa said:**
> 
@wilee-nilee
i might not hav knowledge on certain areas. but i am no inexperienced ubuntu user. ive faced a lot of problems using ubuntu and hav written a lot of how-tos on solving them. many hav followed my how-tos with success. fyi, even this is going to become a how-to.

Good for you.;)

---

