---
title: "Post-installation, Updates hang"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by diamondz123 on 2008-01-08
I am only marginally tech-competent, and I just installed Ubunto 6.06 LTS on what was a no-name P4 machine with badly-behaving XP home edition.

I allowed the install to write over the entire partition (around 160GB).  edition (I think a bootleg edition), so I decided to eliminate to old OS entirely.  

After Unbuntu installed fully, I was prompted to install 186 updates, which I did.  Only one update apparentlyfailed, but I clicked on"okay" and now it has been hanging for 30 minutes ... the only item not grayed-ut in the install box is "app-install-data-commercial."

When I re-booted the machine stops @ "Checking root file system," telling me:

/dev/hda1/ contains a file systen with errors, check forced.
/dev/hda1: Inodes that were part of a corrupted orphan linked list found.
/dev/hda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.

I couldn't figure out howto run fsck manually.  This is pretty disheartening.  Any suggestions?

Steve

---

### Post by PmDematagoda on 2008-01-08
Boot the Ubuntu Live CD and then post the results of:-
```
fdisk -l
```
and
```
cat /etc/mtab
```

---

### Post by diamondz123 on 2008-01-10
> **PmDematagoda said:**
> Boot the Ubuntu Live CD and then post the results of:-
```
fdisk -l
```
and
```
cat /etc/mtab
```

Aloha PmDematagoda!  Thanks for offering to help.

Here's the first one:

------------------
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19079   153252036   83  Linux
/dev/hda2           19080       19457     3036285    5  Extended
/dev/hda5           19080       19457     3036253+  82  Linu

------------------

And here's the second one:

ubuntu@ubuntu:~$ cat /etc/mtab
unionfs / unionfs rw 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-26-386/volatile tmpfs rw 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0

-------------------

As far as I can tell, the hard drive is not showing as "mounted" -- though I'm not sure why/how that happened, nor do I know how to fix it.  I think the install went a bit wonky, but I'm not sure.

I have the same trouble when I tried to install Knoppix!  Both Knoppix and Ubuntu run fine from LiveCDs, but not when I install them.

Any suggestions appreciated.  Is there one good book you'd suggest for a beginner like me?

Namaste!

Steve

---

### Post by PmDematagoda on 2008-01-10
Execute:-
```
fsck -a /dev/hda1
```
After that is complete, try running Ubuntu again.

---

### Post by diamondz123 on 2008-01-14
PmDematagoda,

Thanks once again.  

Okay, I ran that file system check and here is the =long= result.  I have no idea of the meaning of all this ... 

diamondz123

------------------

ubuntu@ubuntu:~$ sudo fsck -a /dev/hda1
fsck 1.38 (30-Jun-2005)
Reiserfs super block in block 16 on 0x301 of format 3.6 with standard journal
Blocks (total/free): 38313008/37801572 by 4096 bytes
Filesystem is NOT clean
Replaying journal..
Trans replayed: mountid 14, transid 819, desc 2284, len 53, commit 2338, next tr ans offset 2321
Trans replayed: mountid 14, transid 820, desc 2339, len 99, commit 2439, next tr ans offset 2422
Trans replayed: mountid 14, transid 821, desc 2440, len 190, commit 2631, next t rans offset 2614
Trans replayed: mountid 14, transid 822, desc 2632, len 99, commit 2732, next tr ans offset 2715
Trans replayed: mountid 14, transid 823, desc 2733, len 2, commit 2736, next tra ns offset 2719
Trans replayed: mountid 14, transid 824, desc 2737, len 15, commit 2753, next tr ans offset 2736
Trans replayed: mountid 14, transid 825, desc 2754, len 10, commit 2765, next tr ans offset 2748
Trans replayed: mountid 14, transid 826, desc 2766, len 1, commit 2768, next tra ns offset 2751
Trans replayed: mountid 14, transid 827, desc 2769, len 19, commit 2789, next tr ans offset 2772
Trans replayed: mountid 14, transid 828, desc 2790, len 31, commit 2822, next tr ans offset 2805
Trans replayed: mountid 14, transid 829, desc 2823, len 261, commit 3085, next t rans offset 3068
Trans replayed: mountid 14, transid 830, desc 3086, len 7, commit 3094, next tra ns offset 3077
Trans replayed: mountid 14, transid 831, desc 3095, len 11, commit 3107, next tr ans offset 3090
Trans replayed: mountid 14, transid 832, desc 3108, len 58, commit 3167, next tr ans offset 3150
Trans replayed: mountid 14, transid 833, desc 3168, len 12, commit 3181, next trans offset 3164
Trans replayed: mountid 14, transid 834, desc 3182, len 64, commit 3247, next trans offset 3230
Trans replayed: mountid 14, transid 835, desc 3248, len 18, commit 3267, next trans offset 3250
Trans replayed: mountid 14, transid 836, desc 3268, len 121, commit 3390, next trans offset 3373
Trans replayed: mountid 14, transid 837, desc 3391, len 101, commit 3493, next trans offset 3476
Trans replayed: mountid 14, transid 838, desc 3494, len 15, commit 3510, next trans offset 3493
Trans replayed: mountid 14, transid 839, desc 3511, len 36, commit 3548, next trans offset 3531
Trans replayed: mountid 14, transid 840, desc 3549, len 27, commit 3577, next trans offset 3560
Trans replayed: mountid 14, transid 841, desc 3578, len 9, commit 3588, next trans offset 3571
Trans replayed: mountid 14, transid 842, desc 3589, len 19, commit 3609, next trans offset 3592
Trans replayed: mountid 14, transid 843, desc 3610, len 13, commit 3624, next trans offset 3607
Trans replayed: mountid 14, transid 844, desc 3625, len 11, commit 3637, next trans offset 3620
Trans replayed: mountid 14, transid 845, desc 3638, len 10, commit 3649, next trans offset 3632
Trans replayed: mountid 14, transid 846, desc 3650, len 10, commit 3661, next trans offset 3644
Trans replayed: mountid 14, transid 847, desc 3662, len 10, commit 3673, next trans offset 3656
Trans replayed: mountid 14, transid 848, desc 3674, len 15, commit 3690, next trans offset 3673
Trans replayed: mountid 14, transid 849, desc 3691, len 16, commit 3708, next trans offset 3691
Trans replayed: mountid 14, transid 850, desc 3709, len 11, commit 3721, next trans offset 3704
Trans replayed: mountid 14, transid 851, desc 3722, len 12, commit 3735, next trans offset 3718
Trans replayed: mountid 14, transid 852, desc 3736, len 10, commit 3747, next trans offset 3730
Trans replayed: mountid 14, transid 853, desc 3748, len 13, commit 3762, next trans offset 3745
Trans replayed: mountid 14, transid 854, desc 3763, len 86, commit 3850, next trans offset 3833
Trans replayed: mountid 14, transid 855, desc 3851, len 18, commit 3870, next trans offset 3853
Trans replayed: mountid 14, transid 856, desc 3871, len 1, commit 3873, next trans offset 3856
Trans replayed: mountid 14, transid 857, desc 3874, len 21, commit 3896, next trans offset 3879
Trans replayed: mountid 14, transid 858, desc 3897, len 111, commit 4009, next trans offset 3992
Trans replayed: mountid 14, transid 859, desc 4010, len 1, commit 4012, next trans offset 3995
Reiserfs journal '/dev/hda1' in blocks [18..8211]: 41 transactions replayed
Checking internal tree..finished

-------------------

ANy further suggestions?

---

### Post by PmDematagoda on 2008-01-14
I believe the problem should be automatically solved. 

Did you try booting up your normal Ubuntu installation?

---

### Post by diamondz123 on 2008-01-15
Aloha PmDematagoda,

Well, thanks once again, but it didn;t work.  I got so frustrated that I installed Knoppix to the hard drive from a LiveCD.  That did not work either, so I re-installed Ubuntu, and when it prompted to whether I wanted to manually partition I said Yes (not knowing what I'm doing), and left it as:

partition #1 of /dev/hda as ext3

partition #5 of /dev/hda as swap

This time it apparently  :KSWORKED:) so all is well.  Of course, I have no idea of how/why it finally worked, but thanks for your help nonetheless.

***However, when I tried to upgrade the 194 upgrades(!), I got an error msg -- and was advised to "use the package manager Synaptic or run sudo apt-get install -f in a terminal.  I did the latter, but I got another rro code:

The following extra packages will be installed:
  perl
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl
Recommended packages:
  perl-doc
The following packages will be upgraded:
  perl
1 upgraded, 0 newly installed, 0 to remove and 180 not upgraded.
Need to get 0B/3297kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 70016 files and directories currently installed.)
Preparing to replace perl 5.8.7-10ubuntu1 (using .../perl_5.8.7-10ubuntu1.1_i386.deb) ...
Unpacking replacement perl ...
dpkg: error processing /var/cache/apt/archives/perl_5.8.7-10ubuntu1.1_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/perl_5.8.7-10ubuntu1.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

--------------

Any other suggestion as I go down the rabbit-hole?  


Cheerio!

diamondz123

---

### Post by PmDematagoda on 2008-01-15
Execute:-
```
sudo rm /var/cache/apt/archives/perl_5.8.7-10ubuntu1.1_i386.deb
```

After that, execute:-
```
sudo apt-get install -f
```

---

### Post by diamondz123 on 2008-01-15
PmDematagoda my good friend!

Much thanks, your suggestions worked!  All updates installed.  Now I can turn the system over to my teenage daughter and see if she can break it!:lolflag:

I just downloaded a couple of Linux/Ubuntu eBooks from our on-line library here in Honolulu, so I'll try to get smart about all this.

By the way, your signature indicates you are in Sri Lanka.  I hope all is well with you -- we do hear about the troubles in your country.  I have long wanted to visit Sri Lanka, as I am a practicing Theravada Buddhist.  I was in Delhi in the 1970s, but never made it out of north India.

Thanks again.

diamondz123

---

### Post by PmDematagoda on 2008-01-15
> Now I can turn the system over to my teenage daughter and see if she can break it!
I wish her(and the Ubuntu install;)) the best of luck:).
> 
I just downloaded a couple of Linux/Ubuntu eBooks from our on-line library here in Honolulu, so I'll try to get smart about all this.
It is much easier than you think, a few months of using Ubuntu can teach you a lot.

> By the way, your signature indicates you are in Sri Lanka. I hope all is well with you -- we do hear about the troubles in your country.
Unfortunately there are troubles over here with the rebels blowing bombs here and there, killing innocent people in the process, I just hope the war ends soon since it has been going on for about a decade or more.

> I have long wanted to visit Sri Lanka
That is nice, I could give you a tour of my beautiful country:).

> I am a practicing Theravada Buddhist.
That is a pleasant surprise, I am a Buddhist myself:).
> 
Thanks again.
Glad to have been able to help:).

---

