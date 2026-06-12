---
title: "[SOLVED] Software RAID1 on 7.04 Feisty Desktop WITHOUT re-installation"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by Midahed on 2007-07-19
For those who might be struggling to get software RAID1 (mirroring) working on Ubuntu 7.04 Feisty Fawn Desktop, WITHOUT doing a re-installation, this may be worth a read....

I installed the desktop version of Ubuntu 7.04 Feisty Fawn on what was my 'secondary'  PC a few weeks ago.  I'm new to Linux, so I spent some time just getting familiar with the Linux environment and slowly moving more and more of my applications and data across from my Windows PC.  Having got to the point where I was happy that the system was reliable, I decided to make the jump and move off  Windows altogether.  The most important of my applications &#8211; my personal finance stuff &#8211; was moved successfully a couple of weeks ago.

So, my 'secondary' PC had become my main machine &#8211; this needed to happen because it's actually newer and faster than my original main machine &#8211; and all my data and applications were running under Linux.  OK, so I do  have Windows on there as well, but that's running under VMware server.

My Ubuntu configuration was the standard 'out of the box' default installation.  In retrospect, maybe I should have started the installation again from scratch before moving everything off Windows, but by that time I'd spent ages tweaking things to my liking, so I chose to stick with my original build.  

That was all OK until I decided I wanted to install a second drive and create a RAID1 environment without the need to re-build the system from scratch.

It is now working (much to my surprise).  In short, I have created a software RAID1 system while preserving all my data and settings and without having to re-build the system.  As I said earlier, the system is based on the default installation of 7.04 desktop .  In other words there is no /boot partition &#8211; just root and swap.  At one point I thought I might have to change this.  I'd read a number of posts where folk trying to do the same thing had given up.  Others said that it was not possible to have a RAIDed system without a non-RAIDed /boot partition.  Not true.  It works just fine.  I can confirm that to be the case.  My system will boot happily off either drive and it only has two partitions.

It has taken me days and days to get this working.  Fortunately I'm retired, so I have the time on my hands and I find that I need the mental stimulation that doing this sort of stuff provides!

Because it has taken so long, I thought it worth writing down my experiences in case it might help anyone else who's trying to do the same thing.

I used to work in IT, so I should be used to making copious notes during a testing phase in order to smooth the process of later doing the same job on a production server.  I'm ashamed to say that my notes are not as good as they should be, so this ain't gonna be some sort of definitive 'how-to' for installing software RAID on a live system.  Sorry about that!  The truth is that I went down so many blind-alleys that my usual care about note-taking went out of the window.

What I will do is point out areas where, as a relative Linux newbie, I got misled by stuff I'd read, or just plain mis-understood what I was supposed to be doing and got it wrong.

I spent hours Googling for documents that would spell out the job for me in simple little steps that I could easily understand, but none really achieved this.  I was occasionally reminded of those times when you're following signs down small rural roads to get to some remote hamlet.  They're reasonably clear until suddenly you arrive at a T-junction with no signs at all!  For a start, most of the good 'how-to' documents on this subject start from the premise that you will be doing a clean install.  Very few try to address the problem of building a RAID1 configuration based on one disk containing a live system installation and its data, and a second blank disk &#8211; they nearly all assume that your starting point is two blank hard drives and an installation CD.

I read dozens of documents on the subject, but in the end there were four that, between them, provided the information I needed to complete the job successfully.

They are (in no particular order):-

1.KingJohn's article in the Ubuntu forums tiitled &#8220;How To Set Up Your Ubuntu 6.06 Server To Run RAID-1 With Live Data&#8221;  [http://ubuntuforums.org/showthread.php?t=470360](http://ubuntuforums.org/showthread.php?t=470360)
  
2.An article to which KingJohn refers, called &#8220;Convert Root System to Bootable Software RAID1 (Debian)&#8221; [http://alioth.debian.org/download.php/668/rootraiddoc.97.htm](http://alioth.debian.org/download.php/668/rootraiddoc.97.htm)

3.An article by Gary V titled &#8220;Software RAID1 (starts degraded), Debian Etch 4.0, kernel 2.6.18, GRUB&#8221;
[http://www200.pair.com/mecham/raid/raid1-degraded-etch.html](http://www200.pair.com/mecham/raid/raid1-degraded-etch.html)

4.An article by D Webber titled &#8220;Setting up software RAID in Ubuntu Server&#8221; [http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

I also needed to refer to the GRUB manual [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)  and also found this page on GRUB very useful as well  [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) 

Finally, there is a bug in Ubuntu that impacts the loading of arrays.  This doesn't cause a major problem because there is a workround which I describe later.  The bug is documented here:-

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/79204](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/79204)
[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/103177](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/103177)

I read them all several times in some detail and then started out using KingJohn's document.  KingJohn's article says perfectly clearly that he is using Ubunto 6.06 server.  He also warns his readers that his instructions may not work in a different environment, with different versions of Ubuntu, etc, etc.

KingJohn's article is excellent &#8211; it, in conjunction with the 'Convert Root System to Bootable Software RAID (Debian)' formed the basis of my approach to the upgrade and gave me loads of pointers to other things I needed to think about....

But there is one big caveat.  I may be wrong about this, but I suspect that the Ubuntu installation CD for desktop and server are different in that the server edition is 'RAID-ready', whereas the desktop edition is not.  This, in retrospect, seems fairly obvious, but my incorrect initial assumption that there were no significant differences tripped me up later in the process.

What does this mean in practice?

KingJohn says at one point early in his 'step 2' that you should install mdadm if you don't already have it on your system.  I recommend that you check this at the very start of 'step 2'.  If it's not there, install it as instructed and then REBOOT.

I had to install mdadm and then tried doing the cat /proc/mdstat to check the 'personalities' output in order to verify that I had a raid-aware kernel.  Because I didn't reboot after installing mdadm, the subsequent cat /proc/mdstat didn't return any results.

When you install mdadm it immediately opens and asks about how it should be configured.  I didn't understand the question, so just accepted the default 'all' response.  My guess was OK, as it turned out!

Another point I would make is that the entire RAID installation needs to be done as root.  There's quite a lot to do, so rather than using sudo in front of every command (and inevitably forgetting it occasionally), I'd recommend that you login as root before you start KingJohn's 'step 2':-

sudo su root
password <your root password>

If you subsequently have to logout or reboot, don't forget to ensure you are root again before continuing the installation.

A few steps into 'step 2' KingJohn suggests you can use the command...

sfdisk -d /dev/hda | sfdisk /dev/hdc

... to copy the partition layout from your live disk to your blank one, but he didn't actually try it in his installation.  I can confirm that it works fine.  I used it, but remember that you have to be root to do it.

KingJohn's instructions assume that you do not RAID your swap partition.  My researches led me to believe that it is better to put up with the additional load on the processor imposed by having a RAIDed swap partition.  You may choose to disagree.  My system has loads of memory and doesn't normally swap, so the overhead is trivial.  Against that, from what I understand, the benefit of a RAIDed swap partition is that the system will continue to run without need for intervention if a disk fails during swap activity.  On the other hand, a failure on a RAID1 system with a non-RAIDed swap can cause the system to crash and require a reboot before it will carry on using the other disk in the RAID1 pair.

If you want to RAID your swap, you'll need to consider that when following KingJohn's instructions.  One of the other articles I recommended does cover RAIDing a swap partition, so the information you'll need can be found there; basically, towards the end of KingJohn's 'step 3', as well as doing...

mkfs.ext3 /dev/md0

...you'll need to do something like...

mkswap /dev/md1

... maybe replacing md1 with your own 'md' number dependent on your partitioning arrangement.

At the very end of 'step 3', KingJohn suggests using...

cat /proc/mdstat 

...to check that the RAID devices exist and that they are all reported as 'degraded' and missing one drive.  Being unfamiliar with all this stuff, I preferred to use...

mdadm --detail /dev/md0

This command reports the status much more clearly &#8211; it actually says 'status clean, degraded'. If you do this rather than cat /proc/mdstat, you'll need to run it separately for each of your array devices, i.e. /dev/md0, /dev/md1. etc.  Unlike cat /proc/mdstat, it only reports one RAID device at a time.

In KingJohn's 'step 4' he copies the data from the original live drive onto the new 'half-RAID' drive.  In my case I only had the root partition to copy &#8211; it would make no sense to copy the swap partition.  However, I did drop down to single-user mode first before doing the copy &#8211; one of the other documents recommended this.

init 1

... wait for the system to go to single-user, then do the copy..

cp -axu / /mnt/md0

My BIG error was to accept at face value the statement in the second paragraph of 'step 5' where KingJohn effectively says there is no need to build a new RAID initrd.  The statement is presumably correct for the server edition (which is what KingJohn's article is based on, and he does make that point very clearly), but I don't believe it applies to the desktop version.

To cut a very long story short, when I later found that I couldn't boot the system using my new 'half raid' disk, I decided that I DID need to build a new initrd image to contain the md and raid1 kernel modules so that they are loaded early enough in the boot process to allow the system to be booted off a RAIDed disk.  One of the other documents I found described a procedure for examining the existing initrd image to see what modules it contained.  In case anyone is interested in checking, it goes something like this:-

cd /tmp
mkdir initrd
cd initrd
cat /boot/initrd.img-`uname -r` | gzip -d | cpio -i

Then examine the content of /tmp/initrd

I did this and could find no trace of the md and raid1 modules in the generic image that's part of the standard **desktop** installation.  Nor were they present if I did a cat /etc/modules

I took this as evidence that the desktop installation would require a new initrd image before it would load, or at least it would certainly require it before it would boot from a RAIDed partition.  In retrospect, it might have been simpler to just create a non-RAIDed /boot partition, rather than go through the subsequent pain of creating a new initrd image, but I chose not to.  I'm not sure, but maybe a separate /boot would have avoided the need to rebuild initrd?

Either way, I decided to build the new image, but made a very serious mistake...

As KingJohn says several times in his document, the 'Convert Root System to Bootable Software RAID1' relates to a very old version of Debian.  Unfortunately, I followed that document when it talks about using mkinitrd to create new initrd images.  BIG MISTAKE!  Although Ubuntu still calls the initrd images something along the lines of initrd.img-2.6.20-16-generic, the default behaviour of mkinitrd is to create a file in cramfs format.  Unfortunately that format is no longer used in Ubuntu, so my newly built image wouldn't work &#8211; it caused a kernel panic instead.  I eventually learnt that the initrd images on the current Ubuntu releases are stored in a gzip'd cpio archive format, and to manipulate them we need to use update-initramfs (which is part of the package called initramfs-tools).  The details of building the new image are very well documented in Gary V's excellent article 'Software RAID1 (starts degraded), Debian Etch 4.0, kernel 2.6.18, GRUB'.

Having sorted out the initrd problems, at this point in KingJohn's 'setp 5', we should have a new 'half-raid' disk that will boot independent of our original live system disk.  The new 'half'-raid' disk is effectively a copy of the original disk, but with RAID support.  However, my PC wouldn't boot off it.  I eventually found that it was all down to changing partition UUIDs &#8211; specifically the ones in /etc/mdadm/mdadm.conf

Due to the way I had copied and rebuilt partitions, combined with the fact that I had installed mdadm on my original live disk and then copied it onto my new 'half-raid' disk along with all the other data in KingJohn's 'step 4', the UUIDs in mdadm (and in /etc/fstab, for that matter) didn't match the real UUIDs for the devices concerned.  Fortunately that's easy to put right.  Run the command...

blkid

...and the system will list all the current UUIDs, something like this...

/dev/hda1: UUID="8d7e5610-a169-4e8b-86b9-b635d82029e4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda2: UUID="25fe2ab2-997a-44bb-b683-2bf26e70cc88" TYPE="swap" 
/dev/hdc1: UUID="bf110005-008d-449b-9ad4-75ed8d66033c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdc2: UUID="c11e562c-832d-461c-855b-840f68684a04" SEC_TYPE="ext2" TYPE="ext3" 
/dev/md1: UUID="c11e562c-832d-461c-855b-840f68684a04" SEC_TYPE="ext2" TYPE="ext3" 
/dev/md0: UUID="bf110005-008d-449b-9ad4-75ed8d66033c" SEC_TYPE="ext2" TYPE="ext3" 

Just ensure that any UUIDs in /etc/mdadm/mdadm.conf and in /etc/fstab are correct &#8211; don't use the ones listed above &#8211; they are unique to a system, so yours will be different.  If, like me, all your partitions are RAIDed, you'll probably find that you don't have to correct any UUIDs in /etc/fstab because you will have commented-out or removed the original partition references and replaced them with /dev/md0, /dev/md1, etc.

There was one more problem to solve before my 'half-raid' drive would boot.  There's a race condition that results in the system trying to read data off the disk before mdadm has finished getting itself ready.  It's all well documented in these two Ubuntu bug reports:-

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/79204](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/79204)
[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/103177](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/103177)

The workround is to cause the boot process to pause for a few seconds in order that the arrays are ready before the system tries to read from them.  You can do this by removing the 'quiet' option in your /boot/grub/menu.lst file and by adding 'break=mount'.  The relevant part of my menu.lst file looks like this:-

title           Ubuntu, kernel 2.6.20-16-generic RAID (hd0)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=/dev/md0 ro quiet=n splash break=mount
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault
boot

title           Ubuntu, kernel 2.6.20-16-generic RAID (hd1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=/dev/md0 ro quiet=n splash break=mount
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault
boot

As you can see, because this is my finished /boot/grub/menu.lst, it now contains entries to allow me to boot from either of my RAIDed pair of disks.

The effect of setting 'quiet=n' and 'break=mount' is that as the system boots you'll see loads of text scrolling up the screen as the system goes through the boot process.  Eventually it will stop because it has reached the point at which it has been told to pause.  When it does so, press the RETURN key and you'll get an initramfs prompt.  Press ctrl-D and the load process will continue normally.  You'll need to do this every time you load the system until there's a permanent fix for this problem

Once I could boot off my 'half-raid' drive, the rest was relatively easy.  I just followed KingJohn's steps 6 and 7 and tidied up /etc/fstab to remove all the previously commented-out lines that referred to the non-raid environment and did the same for /boot/grub/menu.lst.  I also changed the value in field 6 of the /etc/fstab entry for  my root partition to allow the system to periodically check the integrity of the filesystem with fsck.

During the process of building the system I had left it at...

/dev/md0        /       ext3    defaults        0       0

The last zero ensured that the system would not run fsck on the root partition at one of the many reboots during the upgrade.  Once all the work was finished, and the system was fully working, I changed it to a '1'.

/dev/md0        /       ext3    defaults        0       1

Depending on your partition layout, you may want to change the entries for other partitions to allow them to be similarly checked.

Were there any other 'gottchas'?

Well, yes!

First, during the whole process I tried to verify that things were working as expected by taking one drive out of the system.  At times I also wanted to 'protect' my live drive by removing it altogether.  I found that unplugging the drive power, but leaving it connected to the IDE cable caused my motherboard to get a bit confused.  It would sometimes fail to recognise the CD drive (which was on a different channel) and would also screw-up the boot-order in the BIOS.  I'll admit that it's hardly 'best practice' to disconnect the drive power (no, I'm not 'hot-swapping' - I only did it when the system was off!), but I didn't expect it to have that sort of effect.  Once I realised what was happening it was easy to cater for.  Your motherboard may be better behaved than mine, but it might not.  If you're careful, your live disk is pretty safe anyway, so you should be able to leave it in the system, rather than keep removing it &#8211; and, of course, you did take a backup before starting all this, didn't you?

Second, I initially made the wrong assumptions about how GRUB treats drive numbers.  I had to read the two GRUB documents (links near the start of this post) before I understood things properly.

Lastly, after getting the system apparently running OK, I happened to do an fdisk -l and I saw two lines which said something to the effect that /dev/md0 and /dev/md1 did not have valid partition tables.  This had me worried for a few seconds, but of course those are virtual devices, so wouldn't have a partition table.  It's only the physical devices /dev/hda and /dev/hdc, etc that have partition tables.  It's normal behaviour.  Don't panic!

Well, that's about it.  If I knew at the start what I know now, the job would have taken two or three hours, excluding time to take backups.  I hope my experiences might help someone else trying to build a RAID1 system without a re-install.  At least you know it can be done.  I had my doubts about that at times!

Thanks again to the authors of the documents that enabled me (a relative Linux newbie) to get my system RAIDed, especially to KingJohn.

Good luck!

Mike

---

### Post by Luke.Hoersten on 2007-08-11
My /dev/md1 (swap partition) is not actually working. I have 4 gigs for it but when I mkswap, it fails:

> 
sudo mkswap -v /dev/md1 
mkswap: error: swap area needs to be at least 40kB

> cat /proc/mdstat 
Personalities : [raid1] 
md1 : active raid1 sdb3[1] sda3[0]
      3903680 blocks [2/2] [UU]


dmesg is complaining:
> Unable to find swap-space signature

Also, blkid doesn't output the UUID of /dev/md1, only the other drives.
> /dev/sda1: UUID="00a92b3a-c00c-40e3-8136-71cb007e6a24" TYPE="jfs" 
/dev/sda2: UUID="dc41d945-9978-4ef8-ad25-48153b77356f" TYPE="jfs" 
/dev/sda3: UUID="76847f11-b90a-43eb-a71f-abce13081b6c" TYPE="swap" 
/dev/sdb1: UUID="00a92b3a-c00c-40e3-8136-71cb007e6a24" TYPE="jfs" 
/dev/sdb2: UUID="dc41d945-9978-4ef8-ad25-48153b77356f" TYPE="jfs" 
/dev/sdb3: UUID="76847f11-b90a-43eb-a71f-abce13081b6c" TYPE="swap" 
/dev/md2: UUID="00a92b3a-c00c-40e3-8136-71cb007e6a24" TYPE="jfs" 
/dev/md3: UUID="dc41d945-9978-4ef8-ad25-48153b77356f" TYPE="jfs" 


Here is my mdadm.conf:
> # definitions of existing MD arrays
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=46c004ae:64194c2a:59cbb14a:d9cb6217
ARRAY /dev/md3 level=raid1 num-devices=2 UUID=c89964e6:fb5e648f:c05c29cf:1bc2888a
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=458ac06e:d3c9cdbc:9273208c:74ebfb58


Any reason my swap raid drive isn't working?

---

### Post by Midahed on 2007-08-12
In the mkswap error report, it seems to be complaining about your swap space being **too small** - it's saying it has to be at least 40**k**B - note that says 40 _kilobytes_, not gigabytes!.  That seems very odd, especially as /proc/mdstat reports it as 3903680 blocks.

I think I'd start there.  I guess if mkswap is failing, the partition won't be seen as swap space....

The only other difference I can see for the moment is that all my filesystems are ext3, whereas you are using jfs.

Mike

---

### Post by pyers on 2007-09-03
Midahead,  I have hit exactly the same problem as you. I have built a RAD-5 array without too many problems but I am having a nightmare mirroring root. Could you clarify your mdadm.conf file with the UUIDs as demostrated? I have folowed your instructions bu it is still not booting?

TA

---

### Post by Midahed on 2007-09-03
I'm not sure how showing the UUID entries in mdadm.conf will help because, of course, they are unique to an installation.....

The key issue is that the UUIDs for the raid devices in the 'ARRAY' entries in madam.conf are correct - i.e. they match the UUIDs for the raid arrays.

For instance, if I run the command  ```
mdadm --detail /dev/md0
``` I get the following results:-```
 /dev/md0:
        Version : 00.90.03
  Creation Time : Sun Aug 19 14:12:10 2007
     Raid Level : raid1
     Array Size : 196675648 (187.56 GiB 201.40 GB)
    Device Size : 196675648 (187.56 GiB 201.40 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Sep  3 21:32:19 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 36e9fc8f:b938d4de:d8d0742a:5f96a1aa
         Events : 0.10

    Number   Major   Minor   RaidDevice State
       0       3        1        0      active sync   /dev/hda1
       1      22        1        1      active sync   /dev/hdc1
```

The UUID that's reported also needs to appear in the 'array' bit of mdadm.conf:-```
# This file was auto-generated on Thu, 12 Jul 2007 16:12:18 +0100
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=36e9fc8f:b938d4de:d8d0742a:5f96a1aa
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=f017751c:46bbd327:d8d0742a:5f96a1aa
```

Did you read and understand all the various how-tos that I referenced in my post?  My post was not so much as set of instructions as an explanation of the things that originally tripped me up when I was trying to get it working.  You need to read all those how-tos and base your installation procedure on those - not just my post.

What happens when you try to boot?  Do you get an error reported?  Did you install grub?

Are you trying to achieve a mixture of raid 1 and raid 5, or have I misunderstood what you were saying when you said you had raid 5 working but couldn't get mirroring of your root partition to work?

You'll need to provide a bit more information about what you've done and some details of what happens when you try to boot the system before I can offer any other suggestions.

One other thing I should point out... I've had to rebuild my system since I originally got this all working and wrote my original post, so none of the UUIDs that appear in examples of files I post now will tie-up with those in the original post.

Mike

---

### Post by pyers on 2007-09-03
My faullt .. I have a separate RAID-5 array which, frankly was a doddle (even if it did take five hors to sync!)b, consisting of 8 * 500GB drives. The operating system is on a 160GB PATA and it is this that I want to mirror to a second, identical drive. I have followed the Howtos - some of which seem to be conflicting, but mainly the ones by philcore here [http://www.debian-administration.org/articles/238](http://www.debian-administration.org/articles/238) and here: [http://www.debian-administration.org/users/philcore/weblog/4](http://www.debian-administration.org/users/philcore/weblog/4). The system hangs upon reboot immediately after Grub starts to load the OS so it might be one of the issues you describe.

---

### Post by Midahed on 2007-09-04
I know what you mean about conflicting information.  I found the four how-to documents that I referenced in my post gave me all the information that I needed, but I took bits from each one to compile an installation procedure that worked and, more importantly, that I understood what was being done in each step.

If your boot hangs early on in the process, I'd be looking to check that the steps that you took to get a raid-aware initrd image were followed correctly.  I initially had a very similar problem and had to re-read all four how-tos to spot what was going on.

**[Edit]**  You might learn a bit more about where the boot process is failing by putting 'quiet=n' in the appropriate line of your menu.lst file.  There's an example of where it needs to go in my original post.  You'll see a load of messages scrolling up the screen as the system boots.  Hopefully you'll get a clue as to where it's failing.

Good luck!

Mike

---

### Post by pyers on 2007-09-04
What I might do - if its OK by you & with due acknowledgements :-) - is to write a Howto on the process needed to get it to work with this particular flavour of Ubuntu. Although I am realtively new to Ubuntu, I am a professional HP-UX and Solaris administrator which should help me make too many beginners balls-ups!

---

### Post by pyers on 2007-09-04
Ooops ... major Freudian error there. Should read:
What I might do - if its OK by you & with due acknowledgements  - is to write a Howto on the process needed to get it to work with this particular flavour of Ubuntu. Although I am realtively new to Ubuntu, I am a professional HP-UX and Solaris administrator which should help me **AVOID **making  too many beginners balls-ups!

---

### Post by Midahed on 2007-09-04
We all know what you meant ;-)

Yeah - good idea - go ahead.  As I've said already, the main contribution was from the four or five other documents by KingJohn and others that I referenced in my original post on the subject.  They've done the real work - not me.

Having said all that, there is a need for an absolutely definitive how-to on the subject that covers all the angles in sufficient detail that a relative newbie to the world of the command line and Linux doesn't get caught out.  If you're a newbie and you're setting out to raid a live system, it can be a bit daunting if the documentation doesn't explain the installation steps in a lot of detail.  There are plenty of good documents covering a clean installation, but there isn't the same depth of information when it comes to raiding a live system.

It would be a useful document to have around - especially if you could get it adopted by the Ubuntu forum admins and promoted to the official 'how-to' section.  If you have the time to do it, go ahead.

Mike

---

### Post by pyers on 2007-09-09
Got hit by some of the problems you met. The worst one was that although RAID-5 was in the kernel RAID-1 wasn't. This really caught me out since I had got RAID-5 working which implied I should get RAID-1 going ... Like buggery!  Built new kernel (using the method you suggested) and followed the instructions/guidelines  above. Still had problems: mainly due to the system not seeing the root file system - whatever I did I couldn't get past that. The RAID-1 array WAS found but got  no further than that.   I am afraid I gave up at that point and archived the data off the RAID-5 LVs (copied not moved) , umounted the filesystems on the RAD-5, vgchange -a n then  vgexported the VGs.

I then reinstalled the operating system using the **server** version of 7.04 which, although a non-graphical interface, allowed me as* part of the installation* to RAID-1 the operating system partitions. I didn't mirror swap but created two separate swap areas - one on each disk. This shoud allow me to have a swap area always present if a disk fails.

One lovely thing: the 4TB RAID-5 array was detected during install and - as I hoped and suspected - I was able to run a vgimport, vgchange -a y and mounted all my original filesystems that were originally on the system [ yes I had archived the data off anyway  :-) ]feel a bit annoyed that I didn't crack the problem - normally am not beaten by such things but I needed the system back up and running. Took me less that an hour to recover .....

---

### Post by Midahed on 2007-09-09
Mmmmm...  Intriguing.  I wonder why it wouldn't see the root filesystem.  Presumably you did update-initramfs -u after solving the missing RAID1 module issue?  (Apologies if I'm teaching granny to suck eggs, here).  I hate not being able to crack a problem like that.  That's why I was prepared to spend the best part of five days originally getting my system working.  One of the luxuries of retirement, I suppose - no time constraints :)

I sometimes think getting my system working as RAID1 at all was more a case of luck than judgement.  I also nearly gave up at several points.

Presumably the failure to see root wasn't anything to do with those initramfs-tools / mdadm bugs that screw-up the array assembly at boot-time?  Although Launchpad has them as 'fixed', I think that only means there's a fix in source available if you care to re-compile your own binaries.  As far as I can see, the Ubuntu 7.04 distribution (plus all the updates) doesn't include a fix yet.

Mike

---

