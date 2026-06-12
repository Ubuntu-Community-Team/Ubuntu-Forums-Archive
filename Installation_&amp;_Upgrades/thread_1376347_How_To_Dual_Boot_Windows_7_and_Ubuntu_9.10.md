---
title: "How To Dual Boot Windows 7 and Ubuntu 9.10"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by odius420 on 2010-01-09
Hello, well lets start off with me saying I'm fairly new to Linux. I've dabbled in the past with red hat and managed to successfully dual boot that with Windows XP with the boot.ini modification. Now I have Windows 7 Ultimate 32-bit and have been trying to dual boot that with Ubuntu 9.10 desktop i386 with no success. As I'm sitting right now I have a 250 GB drive with a clean install of windows 7. I have the 100MB System partition 70 GB partition for windows itself and the rest is unallocated at the moment. I also have other drives which are not connected right now, just for storing all my data I didn't want to loose right now. Ive downloaded EasyBCD 1.7.2. I've seen a few posts that mention the use of that program, but it hasn't worked for me no matter what I tried. As for my Linux partitions any tips on that would be great aswell. I've been told to keep the / and  /boot seperate. But I'm unsure of the partitions to create, or what partitions should be primary/logical and the sizes and file types to use. If anyone could point me in the right direction as to how to get this working properly it would be great.

---

### Post by odius420 on 2010-01-09
Well that doesn't solve anything. I don't need to upgrade Windows, I know that much...lol. I am not having any problems running Windows 7, it runs quite nice for me. The issue is dual booting it with Ubuntu 9.10 successfully. But thanks.

---

### Post by darkod on 2010-01-09
You don't need separate /boot partition these days, not for home use anyway. Having separate /home partition is good, it allows reinstalling clean on / but still keeping your personal files from /home.
So, something like:
/
/home
swap

/ size is enough 10-15GB depending on hdd space you can spare. Maybe 20GB tops. With all your personal files on separate /home, / doesn't need too much space. Just for information, the standard 9.10 desktop default install takes around 2.7GB and even with software added doesn't grow that much.
swap should be 1.5x your ram, especially if you plan to hibernate. Otherwise, you can make it the same as ram or even smaller depending on ram size. With loads of ram these days swap is even rarely used.
The rest of the hdd space you can spare can go to /home. Have in mind that if putting loads of large files, music, videos, etc in /home then you will need loads of space allocated to it.
This is a quick summary, you can always google for linux/ubuntu partitioning practices.

---

### Post by oldfred on 2010-01-09
You should not need a separate /boot unless you are running an old system with BIOS limits. Some other versions of linux need a separate boot partition.

I have no knowledge of easyBCD. I have seen a few users with it who are primarily windows people and want to keep a windows boot. Grub has worked just fine for me and many users seem ok with it. The new grub2 has a few issues with certain configurations but for most works well.

You do not have to manually partition in advance, I used the standard install for the last 3 years although I did go back and create a shared (Fat then, now NTFS) partition for data that I wanted in both windows and Ubuntu to make it easy to use either with same firefox and thunderbird profiles.

If you have multiple drives I prefer to have an operating system on each drive and that operating system set to boot from the MBR of that drive. Then if there ever is a drive issue I can switch drives in BIOS and still get into my system.

With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

---

### Post by raymondh on 2010-01-09
I would second darko's reco to have a separate /home.  If you're comfortable with creating partitions beforehand and doing a manual install ..... I would definitely go that route.

If not comfortable, you could just install ubuntu using the 'largest continuous free space' selection and let the installer set it up for you (OldFred's suggestion).  

Afterwards, you can try [psychocats' tutorial]("http://www.psychocats.net/ubuntu/separatehome") to separate the /home from root (/)

Back-up your files.

Regards,

Raymond

---

### Post by odius420 on 2010-01-09
Many thanks for the partitioning tips everyone. Now about the dual boot issue. I do have a spare clean drive I could install ubuntu on but its an ATA drive which I can only use in a extenal usb setup but its an old slow drive, so it doesn't run very well. So far that is the only way I've been able to successfully dual boot the 2 systems without problems with it. When i did it that way I just partitioned the drive like I do with my HD0 attempts and it works. Unfortunatley my motherboard only has room for the 2 SATA disks. Upgrading my hardware is out of the question since I don't want to spend money just to dual boot..lol. I suppose I could partition the HD0 and transfer my files from HD1 to it but I don't really want to do that. Would installing linux first make it easier?

@ darkod i saw that boot info script in your signature, would that work after the ubuntu install within the live cd? after i install i cant load ubuntu so im just curious, if so maybe ill try that out and see whats going on with it.

---

### Post by darkod on 2010-01-09
Yes, the boot info script is usually used exactly like that.
You have some problems booting ubuntu from what ever reason, you use the live cd, Try Ubuntu option, download and execute the script and look at the results.txt file. Also you can post the content here for someone else to have a look.

---

### Post by odius420 on 2010-01-09
Ok just found a post you made saying to do exactly what I just asked..lol. so ill do that after I re-install ubuntu and then post my findings here after.

---

### Post by odius420 on 2010-01-09
It seems grub didn't even install I'm assuming.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe7f5fc3a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   143,362,047   143,155,200   7 HPFS/NTFS
/dev/sda3         143,364,060   289,844,729   146,480,670   5 Extended
/dev/sda5         143,364,123   182,418,074    39,053,952  83 Linux
/dev/sda6         182,418,138   280,077,209    97,659,072  83 Linux
/dev/sda7         280,077,273   289,844,729     9,767,457  82 Linux swap / Solaris
/dev/sda4         289,845,248   488,392,703   198,547,456   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________


=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda5


Unknown BootLoader  on sda6


Unknown BootLoader  on sda7


Unknown BootLoader  on sda4



=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda7: No such file or directory
hexdump: /dev/sda7: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
```

---

### Post by darkod on 2010-01-10
You're right, grub2 didn't install. But that's not the main problem. It seems nothing is recognized. You see at the top of the results file where all the partitions are listed it doesn't say known filesystem and OS for any of them.
It can recognize there are different partitions on the hdd but not what's on them.
I'm not sure what happened to be honest.

---

### Post by odius420 on 2010-01-10
yea i have no idea as well...it works fine when i use the external drive. can dual boot with the grub menu and everything. im gunna try it again with the external drive. maybe i missed something i did when i installed it there i dont know..lol.


If i install it through windows would it hurt the performance of linux? or the partition?

---

### Post by darkod on 2010-01-10
> **odius420 said:**
> yea i have no idea as well...it works fine when i use the external drive. can dual boot with the grub menu and everything. im gunna try it again with the external drive. maybe i missed something i did when i installed it there i dont know..lol.


If i install it through windows would it hurt the performance of linux? or the partition?

I really don't like wubi (inside windows install). I can't give you exact info how and why the performance will be affected, but just the fact that wubi is sort of virtual ubuntu is enough for me. Opinions differ, and some people even claim using wubi long term is fine although it was mainly introduced to give windows users a chance to trial how they like ubuntu on the computer without doing any partitioning.
It was never meant as long term install and subsequently is carrying issues with it. It will not work in its own dedicated partition with linux filesystem, etc.

---

### Post by odius420 on 2010-01-10
Ok thanks. I think i may have found the problem. When the partitions are created in the linux install its making them in en extended partition would that effect the running of the system? I'm currently using gparted to make the partitions myself this time and im going to try it that way.

---

### Post by odius420 on 2010-01-10
I'm also wondering, should grub be installed on the MBR with the windows loader? I read a few things that said not to do that since windows writes over it from time to time. So if I am supposed to that would explain my issue.

---

### Post by darkod on 2010-01-10
You can try creating the partitions yourself, but the fact they are logical partitions inside extended one, is not an issue.
Don't forget, you can only have a total of 4 partitions (primary + extended). That's why extended partition was "invented" with logical inside, to make possible to have more than 4 partitions on a hdd.

---

### Post by darkod on 2010-01-10
> **odius420 said:**
> I'm also wondering, should grub be installed on the MBR with the windows loader? I read a few things that said not to do that since windows writes over it from time to time. So if I am supposed to that would explain my issue.

Usually grub is best to be installed on the MBR, overwriting the windows bootloader. There are some exceptions, but usually best on the MBR.

---

### Post by odius420 on 2010-01-10
Haha, ok im doing that now. Thats probably why it wouldn't work with the hd0 partitioned and worked with the second drive installed. Hopefully it works this time :D

---

### Post by Zimmer on 2010-01-10
> **darkod said:**
> Usually grub is best to be installed on the MBR, overwriting the windows bootloader. There are some exceptions, but usually best on the MBR.

I would disagree on this point.. Not familiar with any Win 7 issues BUT ..
I do have a working dual boot of Vista and Ubuntu using EasyBCD.

The advice here
http://www.multibooters.co.uk
http://www.multibooters.co.uk/articles/windows_seven.html
is well worth a read.

I followed the path of :
Vista already installed, used Vista to create space on drive for Ubuntu.
Used Gparted to partition the unallocated space (left the boot flag allocated to the Vista partition).
Installed Ubuntu to the newly created partition AND installed GRUb (when prompted ) to the same partition as the Ubuntu, NOT THE MBR!  

booted to Vista and downloaded and installed EasyBCD. Followed instructions on adding the Ubuntu to the list of boot options with EasyBCD.
Rebooted and got a choice of Vista or Ubuntu, the Ubuntu option took me to the GRUB menu... been booting like that for the last 17 months...
There is more help here
http://neosmart.net/wiki/display/EBCD/Ubuntu

If I were to have Win7 loaded on a PC ( after searching for any other cast iron information) I would attempt the same path to dual boot 9.10 as the WIN7 install would be unaffected provided I DID NOT write GRUB to the MBR.

---

### Post by darkod on 2010-01-10
> **Zimmer said:**
> I would disagree on this point.. Not familiar with any Win 7 issues BUT ..
I do have a working dual boot of Vista and Ubuntu using EasyBCD.

The advice here
[http://www.multibooters.co.uk](http://www.multibooters.co.uk)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)
is well worth a read.

I followed the path of :
Vista already installed, used Vista to create space on drive for Ubuntu.
Used Gparted to partition the unallocated space (left the boot flag allocated to the Vista partition).
Installed Ubuntu to the newly created partition AND installed GRUb (when prompted ) to the same partition as the Ubuntu, NOT THE MBR!  

booted to Vista and downloaded and installed EasyBCD. Followed instructions on adding the Ubuntu to the list of boot options with EasyBCD.
Rebooted and got a choice of Vista or Ubuntu, the Ubuntu option took me to the GRUB menu... been booting like that for the last 17 months...
There is more help here
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

If I were to have Win7 loaded on a PC ( after searching for any other cast iron information) I would attempt the same path to dual boot 9.10 as the WIN7 install would be unaffected provided I DID NOT write GRUB to the MBR.

I never said it's the only way it will work! If you want to use third party bootloader that didn't come with either windows or ubuntu, your choice.
What is getting me slightly annoyed is that after following advice like this if people get into trouble with EasyBCD they come here for help, not on the windows or easybcd forums. And what has ubuntu got to do with the choice they made to use easybcd? And I've seen threads like that here. Just don't blame ubuntu later. :)

---

### Post by odius420 on 2010-01-10
Still not working. the HD seems to be naming itself /dev/mapper/nvidia_hdbchadbe is that normal for this? Im seeing both /dev/sda and /dev/mapper/nvidia_hdbchadbe in the gparted /dev list. but when I install ubuntu it only shows the other. And when I tried to install grub to the MBR its still just loading right to windows. Also its seems devkit-disks-daemon keeps getting an application problem closing it, that wouldn't have anything to do with my problem would it?

---

### Post by darkod on 2010-01-10
> **odius420 said:**
> Still not working. the HD seems to be naming itself /dev/mapper/nvidia_hdbchadbe is that normal for this? Im seeing both /dev/sda and /dev/mapper/nvidia_hdbchadbe in the gparted /dev list. but when I install ubuntu it only shows the other. And when I tried to install grub to the MBR its still just loading right to windows.

It would be "normal" if you have a setting in BIOS for enabled raid. On every restart it would "try to make" the hdd a raid member.
Look carefully trough BIOS, disable any raid settings, and then only once removing dmraid is enough from what I've seen.

---

### Post by darkod on 2010-01-10
Sorry, I got confused with another thread I was replying to. If you have /dev/mapper/blabla device shown that means raid traces on the hdd. 9.10 can pick them up and it's confusing ubuntu thinking your drive is raid member.
If you are NOT running any raid, just boot with ubuntu cd, Try Ubuntu option, and in terminal execute:
sudo apt-get remove dmraid

Reboot and see how it goes. Because you already had ubuntu installed with this setting active, I'm not sure whether you have to reinstall ubuntu again or just reinstalling grub2 would be enough. Try how it's working after removing dmraid, if not working OK try reinstalling just grub2 first, and the next step is full reinstall of ubuntu.

PS. Of course, you need to have any raid settings in BIOS disabled.

---

### Post by odius420 on 2010-01-10
Ahh ok sweet. now im seeing sda and what not thnx.

---

### Post by odius420 on 2010-01-11
well nothing worked but i did notice this:

My first partition seems to have a problem I never noticed before. could that be why its im having these issues? if so im not sure how to correct this. I assume a fresh windows install, but thats how i got that mess in the first place. maybe a crap .iso image?

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe7f5fc3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
[SIZE=2][COLOR=Red]_**Partition 1 does not end on cylinder boundary.**_[/COLOR][/SIZE]
/dev/sda2              13        8924    71577600    7  HPFS/NTFS
/dev/sda3            8925       21035    97281607+   7  HPFS/NTFS
/dev/sda4           21036       30401    75232395    5  Extended
/dev/sda5           21036       23467    19535008+  83  Linux
/dev/sda6           23468       29789    50781433+  83  Linux
/dev/sda7           29790       30401     4915858+  82  Linux swap / Solaris

```

---

### Post by oldfred on 2010-01-11
That entry is normal for Vista and windows 7. Linux and XP started at sector 63, but Vista & 7 start at 2048 which is not a cylinder boundary.

I thought that darko's solution worked. I have also seen this but you will have to temporarily add dmraid back in. It is my understanding that this removes the raid setting hidden on the hard drive that causes the problem.
sudo apt-get install dmraid

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
then so it cannot look for raid
sudo apt-get remove dmraid

---

### Post by odius420 on 2010-01-11
Finally, that was the problem. The HD had hidden raid settings on it. Followed Presence1960's removal and everything boots up great now. Grub is loading good and the dual boot options are there. Thanks a bunch everyone. Hopefully down the line I can repay the favor to someone else :D.

---

