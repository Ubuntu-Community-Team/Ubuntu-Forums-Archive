---
title: "Installer problem: &quot;no OS&quot;"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by jombra on 2010-03-12
Hello,

I am new to this forum and quite new with Ubuntu either, though I am a professional
Unix administrator [and used a 5 years old Debian with just new vanilla kernels
before I switched to Ubuntu with my new laptop (Intel Core2 Duo T6400@2GHz, 3 GB RAM,
Intel GM45 Express Chipset) last year ;-)].
I currently use Ubuntu 9.04 on my private laptop 99.9% of the thime.
Unfortunately, the internal Intel chipset graphic (GMA 4500) shows problems with
the external HDTV display, so I need to install 9.10 (as 10.4 will last somewhat).

I tried several times to install Ubuntu 9.10 - also different flavors - and always
being forced to stop when partitioner comes into play.
Ridiculously it thinks that there is no OS on it - I have a 500 GB internal disk
with several OSs on it - all booting fine - and "fdisk -l" yields:

=== ***
  Device    Boot      Start         End      Blocks   Id  System
  /dev/sda1   *           1         128     1028128+   6  FAT16
  /dev/sda2             129        3393    26226112+   7  HPFS/NTFS
  /dev/sda3            3394        4002     4891792+  82  Linux swap / Solaris
  /dev/sda4            4003       34768   247127895    5  Extended
  /dev/sda5            4003        8016    32242423+  83  Linux
  /dev/sda6            8017       12030    32242423+  83  Linux
  /dev/sda7           12031       15678    29302528+  83  Linux
  /dev/sda8   *       15679       15763      682731   83  Linux
  /dev/sda9           15764       18903    25222018+  8e  Linux LVM
  /dev/sda10          18904       19328     3413781   83  Linux
  /dev/sda11          19329       56787   300889386   83  Linux
  /dev/sda12          56788       58795    16129228+  83  Linux
  /dev/sda13          58796       60801    16113163+  83  Linux
--- ~~~
with old (original Ubuntu 9.04) grub residing on the MBR and Windows bootloader on sda1
(booting IBM DOS2000 or XP - last was included with my laptop) with Ubuntu booting
from sda7 - sda5,6,12,13 being empty (new HDD - OSs will follow), sda11 being
home2 for all Linux derivates.
=== ***

Now all I want is to install 9.10 in the empty sda5 (with new ext4 FS) and
latest Grub (2-beta) to the MBR - hopefully customizable for my needs.

The options the standard installer gives me is to install Ubuntu 9.10 to the entire
disk {well, normally the default mode set by Windows :)} or totally repartition
the HDD - both are no options for me.

I am still pretty sure to miss something - such a bug could not escape a beta test
and I do upload latest ISOs and have also got an Ubuntu magazine (UBUNTU user 02/2010,
Germany) with DVD to be sure.

With other minor problems the solution could be googled in seconds -
unfortunately with this problem I could not find any solution - or
even a hint to a known installer bug.
But as said before I am not familiar with the Ubuntu community or bug reports for
any Ubuntu derivative - but that may change in near future.

Any hint and workaround is highly appreciated.

Thanks in advance!

---

### Post by pastalavista on 2010-03-12
If you're using a live CD, boot from it first (try without changes...) and run fdisk from there. Use gparted to make sure the partition is ready and try the installer on the desktop... if you haven't done so already

---

### Post by Arand on 2010-03-12
Does the installer show the separate partitions correctly though? Is it only the detection of OS names that is askew or is there something else going on so that it doesn't detect the partition structure?

If partitions are detected...:
It sounds like you would need to go into manual partitioning an define the partitions and mountpoints manually in the installer (You'll need at least "/", swap will probably be associated automatically (select "don't use" and create new swap if you want separate swap))
So in the "manual" screen select sda5, click "change" select "use as" -> ext4, select "mountpoint" -> / , and that should be it. 

Either that, or you could remove (via e.g. gparted) the partition residing in the place where you intend to install to.
Then the option to "use largest continuous free space" should become available in the installer and ubuntu will automatically create a "/" and swap (or use already existing swap, I'm not certain as to what is the default there) there and install.

 - Arand

---

### Post by jombra on 2010-03-12
Thanks for your message,

I used install mode and live mode with the installer icon - both the same.
I just checked that fdisk - also with live cd - shows the above partition table,
but I do not make changes - the partitioning is correct.

P.S.: Concerning the post #3 - no, the installer says no OS and in advanced mode for editing
partitioning only sda is shown, no partition information (I've seen a screenshots how it should
look - but for me the partition table is blank - and one continuous bar for the HDD is displayed).

I think any flag to the partition table to activate or so is done by the installer - and doing
it by hand may have strange side effects. If the installer needs such help, could someone
give a recipe how to do it?

---

### Post by Arand on 2010-03-12
I know there have been similar problems related to the dmraid package.

So if the partition you intend to install to is not part of a fakeraid, you could try to remove the package:```
sudo aptitude remove dmraid
```which might make the installer detect the partitions properly again.

Alternatively, you could check if using the alternate install CD works better.

- Arand

---

### Post by jombra on 2010-03-12
I am not using RAID - a Samsung laptop with Intel chipset, so a quite
easy and common configuration for Linux - but as the booting CD/DVD-images
do have problems the package removal should be done there - if possible -
right?
I can later test if that works.

What Do you mean by "alternate install CD" - I tried Ubuntu (CD+DVD) and
Xubuntu with the same result - I reflected upon testing 64-bit server,
but I don't see that the situation may change a lot.

Concerning post #3 - I overlooked the end to try removing a partition.
I can remove sda5 as its empty anyway - but why should the installer see
an empty region if it totally neglects the entire partition table anyway?

---

### Post by jombra on 2010-03-12
I am back again.
As was proposed above I just deleted sda5 (I should not have done that,
see below - don't try this if you have similar problems and don't want
to get some more) to see if that has an effect on the partitioner /
installer.
Of cause not - it still shows one brown bar for the HDD without any other
parts and still is sure that there are no OSs on the system.
Also "Specify partitions manually (advanced)" does not help - no
partition, only sda as a whole.
Now I tried "sudo aptitude remove dmraid" on my live system - it was
successfully removed - but the installer still could not see any
partition.
Well - on that stage I was not so amused - but one may guess that this is
not over here - as grub, configured via Ubuntu 9.04 residing on sda7 now
sda6 (as sda5 was deleted) could not find its configuration - and stopped
with error 15.    :-o
Yipiyaoooooooooooooo!
Creating a new partition with limits of the former sda5 does not help,  :(
as this automatically gets label sda13.  ;-)
So I had to install the nice old bootloader via grub-install from the
original 9.04 live CD - always welcome.
So in this case - I am really back.
In case no one can help me with the problem directly
one may give me a hint to file a bug report.
I don't know why there are not plenty of other people with this problem
but nevertheless ... I would like to hear from experts with the
installer/partitioner {duo infernale :)} what's going on there - and
to fix it.
The only 2 ways for me out right now (getting a new X.org and Ubuntu base)
is trying Mint 8 (does it have the same installer/partitioner?) or trying
10.4 - deep in alpha.
I don't feel comfortable with either ... as I have to work with and rely on
that system.
Any help is really welcome !!!

---

### Post by jombra on 2010-03-14
Ok, installing 10.4-A2 didn´ t - like Mint 8.
When starting gparted from the command line shows the problem:
---
sudo gparted
[sudo] password for jbraun:
======================
libparted : 1.8.8
======================
Can't have overlapping partitions.
---
From my point of view a GUI not showing a bug but pretending
a correct result is a more severe bug than a crashing program.
I can understand that several people feel bitter with the installer/
partitioner ...
In my case the partition table was corrupted (it was OK at 1st time,
no idea what changed that - you can see it in my 1st posting - the
extended partition is just the middle of the HDD, not the entire rest
after the 3 primary partitions) and I fixed it by blanking the partition
table with testdisk (being part of Ubuntu 9.04) and redoing the correct
partitioning with fdisk (one should be careful with that - this is for
experienced useres - others may be better off letting testdisk correct
the partition table - and total data loss is possible).
Now I was able to install Karmic Koala (aka 9.10) in parallel to my
existing Jaunty Jackalope (aka 9.04) - and just start to fight with
the configuration.
I found the solution here in the forum - in an article dating April 2007:
  [http://ubuntuforums.org/showthread.php?t=413745](http://ubuntuforums.org/showthread.php?t=413745)
So the misleading info "no operating system" and showing the disk as one
chunk is a `good´ old tradition ...
Maybe this can help someone who gets caught by this problem like me.

---

