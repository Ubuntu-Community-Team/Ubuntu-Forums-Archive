---
title: "Installing Ubuntu 11.10 alongside Windows 7 [No Wubi]"
date: 2011-10-10
forum: Installation &amp; Upgrades
---

### Post by anantanni on 2011-10-10
I have partitioned 20 GB unallocated space for Ubuntu 11.10 (Which is coming out on 13th oct. 2011)

I'm not going to use Wubi.

So can anyone here please tell me how to install ubuntu in that Partition without effecting/deleting/corrupting the Windows?

Thanks in Advance



**EDIT**!

**Wrong Section**! Please delete, and sorry.

---

### Post by anantanni on 2011-10-10
So I'm going to install the Ubuntu 11.10 Oneiric Ocelot to my Dell Latitude D520 System.

I have ran Ubuntu before on it. So I kinda know the Installation Process.

I have pre-installed Windows 7 Ultimate, I don't want to delete it. So I have partition 20gb unallocated space on my harddrive for ubuntu.

Can anyone tell me how to install it alongside windows 7(Dual Boot)?:popcorn:


P.S. Loving this smiley:guitar:

---

### Post by PeteAsdf on 2011-10-10
Hi,

Just burn the installation CD, pop it in, reboot and follow the instructions. Installing Ubuntu alongside windows is pretty easy, the installation wizard will guide you through it.

Good luck

---

### Post by bloodorange on 2011-10-10
As long as you make sure you install Ubuntu into the spare 20GB space, the install process will sort out the dual boot for you.  Back up your Windows data first, though, just to be safe.

---

### Post by sanderd17 on 2011-10-10
Normally you should get the option "use empty space" during the install process.

If you don't get that option, tell it to us, that means some manual partitioning has to be done.

---

### Post by raja.genupula on 2011-10-10
while doing the installation process you will get a window which includes the partition choose.In that you are going to have 4 options , in that choose last one(manual or custom) and then in the next window choose your free space for the ubuntu.then remaining steps are common.

All the best.

---

### Post by raja.genupula on 2011-10-10
hi while doing the installation process 1st and last option will help you to install Ubuntu at the time of selecting the partition.1st option is what you wanted.last option is doing manual allocation(because you mention that you have 20gb free space to install).In the manual allocation you can use that 20gb for your ubuntu.I suggest manual will be better.

All the best.

---

### Post by garvinrick4 on 2011-10-10
Towards the bottom of the first link I have given you it shows you how to
install in a partition you have already made in graphics in the Ubuntu installer Ubiquity.

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
[HowToPartition - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowtoPartition")
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by Rubi1200 on 2011-10-10
anantanni,
I have merged your 2 threads into one; makes life easier for all of us :)

---

### Post by PayPaul on 2011-10-11
I want to completely reinstall both Windows 7 and Ubuntu. I may use my current liveCD with Natty to do the Ubuntu install or perhaps opt for the new release. What I also need to do is to format all 3 partitions on my main drive. The first partition will be for a clean install of Win7, the second is planned for Windows Program Files and the third is planned for the Ubuntu Installation. Can I reformat all these partitions from the LiveCD using Gparted? Currently I have an install of Win7 on the first partition and that didn't install correctly hence a need for an absolutely clean reinstall. I also know never to try to install Ubuntu before Windows. What's the best method for doing this?

---

### Post by Frogs Hair on 2011-10-11
I use Windows disk management to create the space and use that space during the Ubuntu installation . 

Reinstalling Windows makes life much easier , just install Windows and use disk management  create the partitions . There plenty of guides available .

---

### Post by PayPaul on 2011-10-11
> **Frogs Hair said:**
> I use Windows disk management to create the space and use that space during the Ubuntu installation . 

Reinstalling Windows makes life much easier , just install Windows and use disk management  create the partitions . There plenty of guides available .

My problem is that my current Windows 7 installation refuses to start properly if at all. Can I use Gparted from a LiveCD to format the existing partitions? Then I'd reboot to the Win7 install disk, install that on the first reformatted partition and then reboot again after all that drama is over and install Ubuntu onto another existing partition.

---

### Post by BobMarleyy on 2011-10-11
> **PayPaul said:**
> I want to completely reinstall both Windows 7 and Ubuntu. I may use my current liveCD with Natty to do the Ubuntu install or perhaps opt for the new release. What I also need to do is to format all 3 partitions on my main drive. (...) What's the best method for doing this?

In my experience it is easier to create partitions before installing.
Usually I create all my partitions in Ubuntu before (re)installing anything. There is a disk utility to do this. Since your windows isn't working properly, just completely erase that partition. Then install your new windows on that partition, next to ubuntu. Finally, start installing the new ubuntu, replacing the old one!
So here are the steps:
1. start ubuntu and completely remove all data on the windows partition
(1b. create an extra partition reducing the size of the windows partition)
2. install windows on your emptied partition
3. install ubuntu onto the ubuntu partition
(3b. create an extra partition reducing the size of the ubuntu partition)

I hope this helps

PS Recently I stopped dual-booting windows and ubuntu, because I like how you can do a complete windows install within ubuntu using virtualbox [https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by PayPaul on 2011-10-11
> **BobMarleyy said:**
> In my experience it is easier to create partitions before installing.
Usually I create all my partitions in Ubuntu before (re)installing anything. There is a disk utility to do this. Since your windows isn't working properly, just completely erase that partition. Then install your new windows on that partition, next to ubuntu. Finally, start installing the new ubuntu, replacing the old one!
So here are the steps:
1. start ubuntu and completely remove all data on the windows partition
(1b. create an extra partition reducing the size of the windows partition)
2. install windows on your emptied partition
3. install ubuntu onto the ubuntu partition
(3b. create an extra partition reducing the size of the ubuntu partition)

I hope this helps

PS Recently I stopped dual-booting windows and ubuntu, because I like how you can do a complete windows install within ubuntu using virtualbox [https://www.virtualbox.org/](https://www.virtualbox.org/)


Disk Utility? Is it Gparted? I don't see a need to reduce the size of any of the partitions. Windows 7 needs the larger size partition. I might consider dividing up the 3rd partition into two parts, one for Ubuntu and the other for data storage. 

I'm not too keen on Virtual Machines. Wubi is almost like that too and can be problematic at times. I can only imagine how badly Win7 will operate.

---

### Post by garvinrick4 on 2011-10-11
Some use Disk Utilily some use gparted choose the tool you like, I use gparted just
because I always have. I keep a gparted CD burned from gparteds .iso around also.
Keep your data storage in NTFS if you want and it will be a letter in Windows system
and a sda# in Ubuntu so as to use same. Make your partitions as you want. Windows
in primarys and a extended so as to make logicals for Linux and all else. Install Windows
first and Ubuntu second and put grub always in sda not sda1 or sda5 but always sda and
you will be fine.
 I will give you a good hint if interested in learning quickly. While in Forums and you see
user that is excellent on subject you are interested in ( they usually have written tutorials also on subjects also) 
just kind of grab onto coat tails for a while and follow his or hers posts around and read them and study any tutorials 
around (usually in their signatures.) There are lots of ways to get around these Forums and lots of Searches can be done. 
You will find that a lot of users get one subject that they really excel in, use that to your advantage. 
These Forums have a lot of learning advantages, not just to answer questions. Using Google search is 
also very much needed as to learn. What ever you learn put into practice so is just not in theory but something in practice and understood. 
I seem to always have kept one install at least just to be my guinea pig or testing install. It is really up to user and how much they want to learn about Linux and 
Ubuntu in particular. Using two different distro's at first jump into Linux can be a bit confusing the apt-get's and the yum's or zyppers 
and such are just different to learn would suggest learning your Ubuntu first then if want to see what the yum's are all about
give RedHat and its cousins a look. Post getting long in the Tooth, enjoy your Ubuntu. Oh and keep Tomboy notes so as to always have what learned until memorised, I
seem to forget things right after I learn them anymore and have to drill them into my Noggin.
## Gave you a how to partition link in previous post.

---

### Post by Mjchopperboy on 2011-10-11
> **PeteAsdf said:**
> Hi,

Just burn the installation CD, pop it in, reboot and follow the instructions. Installing Ubuntu alongside windows is pretty easy, the installation wizard will guide you through it.

Good luck

True, you will have a big, huge button with a choice between next to windows, on windows or... I don't remember what else.

---

### Post by PayPaul on 2011-10-11
That was a wonderfully long post with a good deal of helpful info in it. I've been subscribing to oodles of threads in here especially those with juicy bits of command line that have come in handy and will in future. Tomboy notes has a funky method of doing things and my prefs are for creating a document in Libre Writer. I usually put the actions and results of terminal commands in that. I have been finding terminal commands much more effective at controlling program behavior than anything else I've seen. I am thinking I'll use and have to use Gparted on a LiveCD. There's no way I can format the partition that contains Win7 from inside my Wubi install of Ubuntu is there? Not that I mind the LiveCD. It saved my skin along with using a couple of command lines involving mounting the root.disk file when I screwed up the disk space over the weekend. When you spoke of people to watch I know for certain that BCBC is one to do that with. He has loads of knowledge, not condescending about it and responds very quickly with clear, succinct answers. 

From what I've been reading about the latest release it's a mixed bag and I think some people are cynical. Amazing to find that's possible with this OS but I've also seen what can go wrong. Just like with any OS there are bugs and conflicts that go on. Oh, I do love it how Ubuntu(Linux as well?) calls them "dependencies". It's a much more clearer term for what they do than .dll. I used to call those the dills that put me in a pickle. The synaptic manager is also often my best bet for making sure a program/package installs correctly including those dependencies.

Thanks a lot for the advice.

---

### Post by garvinrick4 on 2011-10-11
> When you spoke of people to watch I know for certain that BCBC is one to do that with Yes if it is all things WUBI you want to learn bcbc and rubi1200 are the ones
to know. When you are rummaging through these Forums and wanting to know about a certain topic you will find others that are efficient in all different phases of Ubuntu. bcbc
is great user to follow has a lot of knowledge. Take care and if you get in a pickle with
any part of partitioning post here will keep subscribed. Once you get that there are just
3 partition Primary, Extended and Logical and sda1 thru sda4 are primary and sda5 and up
are logical and Extended is just a house for all your Logicals it gets easier all the time.
Only 4 Primarys allowed and the one Extended counts as a Primary.

---

### Post by john bengston on 2011-10-11
I get an invalid argument message when I try to install ubuntu 11.4 on a windows xp computer using a cd.
I just got done using daemon tools without using cd and it works. Apparently my cd-rom reader is not able to read the cd disk. Ive used another cd with ubuntu 9.10 on it and it does not give me that error. I will try to burn another ubuntu 11.4 but will use a slower speed like 4x instead of 10x. and see if that works better.

---

### Post by garvinrick4 on 2011-10-11
Welcome to the Forums john bengston start a new Thread and put Wubi in Title 
and highlight the whole thing and hit the # sign and will put in a nice box to read
from and not take up so much space.

---

### Post by PayPaul on 2011-10-11
I'd edit that post by clicking on edit, use control X and then put the following in [COLOR=Red]```
 
```[/COLOR] and paste in between the space between. The [COLOR=Red]/[/COLOR] ends the code box.

It did take me about a week to figure out how to do that as well. it's hand for just about any kind of long text like that. It produces the scroll bar as well that I'm sure you've seen on some threads already.

---

### Post by PayPaul on 2011-10-11
> **garvinrick4 said:**
>  Once you get that there are just
3 partition Primary, Extended and Logical and sda1 thru sda4 are primary and sda5 and up
are logical and Extended is just a house for all your Logicals it gets easier all the time.
Only 4 Primarys allowed and the one Extended counts as a Primary.

My main drive has a strange malady. It's read in Gparted not as [COLOR=Blue]sda[/COLOR] but [COLOR=Blue]sde[/COLOR]. Weird. Why would that be? I've the niggling suspicion it is either symptomatic of some of my pc troubles prior to this install of Ubuntu or it may be part of what's causing the busybox issue at boot. There's a UUID that is indicated as invalid... but I don't want to get too off topic here.

---

### Post by dFlyer on 2011-10-11
> **anantanni said:**
> So I'm going to install the Ubuntu 11.10 Oneiric Ocelot to my Dell Latitude D520 System.

I have ran Ubuntu before on it. So I kinda know the Installation Process.

I have pre-installed Windows 7 Ultimate, I don't want to delete it. So I have partition 20gb unallocated space on my harddrive for ubuntu.

Can anyone tell me how to install it alongside windows 7(Dual Boot)?:popcorn:


P.S. Loving this smiley:guitar:

Please go to this link:  [http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Click on all the link on this page and read them. Ubuntu is very easy to install, but do the research first.

Once you have decided to install linux, make sure you back up what ever OS you're currently using. Just remember linux is not your other OS so go slow, have fun and when problem pop up ask questions.

---

### Post by garvinrick4 on 2011-10-11
> It's read in Gparted not as [COLOR=Blue]sda[/COLOR] but [COLOR=Blue]sde[/COLOR].
Have you ever run a boot_script.
Now would be the time to see whats up on your drive.
[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") 
Download to Desktop and extract by right clicking and using "archive manager"
and then run this code and post results.
```
sudo bash ~/Desktop/boot_info_script.sh
```

---

### Post by PayPaul on 2011-10-11
> **garvinrick4 said:**
> Yes if it is all things WUBI you want to learn bcbc and rubi1200 are the ones
to know. When you are rummaging through these Forums and wanting to know about a certain topic you will find others that are efficient in all different phases of Ubuntu. bcbc
is great user to follow has a lot of knowledge. Take care and if you get in a pickle with
any part of partitioning post here will keep subscribed. Once you get that there are just
3 partition Primary, Extended and Logical and sda1 thru sda4 are primary and sda5 and up
are logical and Extended is just a house for all your Logicals it gets easier all the time.
Only 4 Primarys allowed and the one Extended counts as a Primary.

> **garvinrick4 said:**
> Have you ever run a boot_script.
Now would be the time to see whats up on your drive.
[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") 
Download to Desktop and extract by right clicking and using "archive manager"
and then run this code and post results.
```
sudo bash ~/Desktop/boot_info_script.sh
```

Here is my last Boot script I did a few weeks ago. The 500gb drive, sde is the main internal drive on my machine. The others are all external usb drives.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sde2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr

sde4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sde5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sde5/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048 3,907,024,895 3,907,022,848   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,302,343,679 1,302,341,632   7 NTFS / exFAT / HPFS
/dev/sdb2       1,302,343,680 2,604,685,311 1,302,341,632   7 NTFS / exFAT / HPFS
/dev/sdb3       2,604,685,312 3,907,024,895 1,302,339,584   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   778,654,484   778,654,422   7 NTFS / exFAT / HPFS
/dev/sdc2         778,654,485 1,465,144,064   686,489,580   7 NTFS / exFAT / HPFS


Drive: sde _____________________________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sde2             206,848    65,538,047    65,331,200   7 NTFS / exFAT / HPFS
/dev/sde3          65,538,048   219,138,047   153,600,000   7 NTFS / exFAT / HPFS
/dev/sde4         219,138,048   976,771,071   757,633,024   f W95 Extended (LBA)
/dev/sde5         219,140,096   976,771,071   757,630,976   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       00f8a910-f8d1-42b3-8df0-063ea1c858fd   ext4       
/dev/sda1        402C6F232C6F12E8                       ntfs       Elements
/dev/sdb1        C018134E181342B8                       ntfs       Free Agent Files And Videos
/dev/sdb2        56BE6AA4BE6A7BFD                       ntfs       Photos
/dev/sdb3        10309D75309D6290                       ntfs       Photos And Videos II
/dev/sdc1        8A8805C68805B22D                       ntfs       Jellybabies
/dev/sdc2        34D451CBD4518FCA                       ntfs       SarahJane
/dev/sde1        16B89432B89411FB                       ntfs       System Reserved
/dev/sde2        765249145248DB0F                       ntfs       Program Files
/dev/sde3        F8A4BC21A4BBDFF4                       ntfs       
/dev/sde5        BEB23740B236FD09                       ntfs       Data And Documents

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/Elements          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/Free Agent Files And Videos fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/Photos            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb3        /media/Photos And Videos II fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/Jellybabies       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc2        /media/SarahJane         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sde5        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


======================== sde5/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root BEB23740B236FD09
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-11-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root BEB23740B236FD09
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=BEB23740B236FD09 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, Linux 2.6.38-11-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root BEB23740B236FD09
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=BEB23740B236FD09 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root BEB23740B236FD09
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=BEB23740B236FD09 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root BEB23740B236FD09
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=BEB23740B236FD09 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 16B89432B89411FB
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

============================= sde5/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sde5/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   4.254676819 = 4.568424448    boot/grub/grub.cfg                             1
  25.754463196 = 27.653644288   boot/initrd.img-2.6.38-11-generic              3
   2.508926392 = 2.693939200    boot/initrd.img-2.6.38-8-generic               2
  25.597969055 = 27.485609984   boot/vmlinuz-2.6.38-11-generic                 1
  12.258090973 = 13.162024960   boot/vmlinuz-2.6.38-8-generic                  1
  25.754463196 = 27.653644288   initrd.img                                     3
   2.508926392 = 2.693939200    initrd.img.old                                 2
  25.597969055 = 27.485609984   vmlinuz                                        1
  12.258090973 = 13.162024960   vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdd 


```

That script is one long puppy. Glad for the code script in this forum.

What do you make of it?

---

### Post by garvinrick4 on 2011-10-12
3 drives that are used for data, no operating systems no boot files. 1 drive sde following
sdc no sdd and has Windows 7 and a Wubi install of Ubuntu inside of Windows on sde. 
> menuentry "Windows 7 (loader) (on /dev/[COLOR=Red]sda1[/COLOR])" --class windows --class os 
{     insmod part_msdos     insmod ntfs     set root='(/dev/sda,msdos1)'     
search --no-floppy --fs-uuid --set=root 16B89432B89411FB     chainloader +1> menuentry "Ubuntu, Linux 2.6.38-11-generic" 
{     insmod part_msdos     insmod ntfs     set root='([COLOR=Red]/dev/sda,msdos5[/COLOR])' 
    search --no-floppy --fs-uuid --set=root BEB23740B236FD09
 loopback loop0 /ubuntu/disks/root.disk     set root=(loop0)
 linux /boot/vmlinuz-2.6.38-11-generic root=UUID=BEB23740B236FD09
 loop=/ubuntu/disks/root.disk ro   quiet splash     initrd /boot/initrd.img-2.6.38-11-genericSeems at install this drive was sda and not sde must have done some switching around with drives.

---

### Post by PayPaul on 2011-10-12
So is there a way to switch the main drive from the designation of sde back to sda? Would this be the source of my busybox issue at boot?

---

### Post by wildmanne39 on 2012-11-21
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

