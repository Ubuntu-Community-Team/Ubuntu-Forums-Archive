---
title: "Getting Ready To Install Ubuntu"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by UltraM4n on 2006-10-16
Hello Folks! This is My First Linux installation onto a hard drive ( i have a copy of the knoppix live cd) and i'm not sure about this partoning. Is it possible i could get some picture tutorials? Thanks In Advanced.



Also My Computer Specs.

Intel
Pentium 4 CPU 2.66ghz
2.66 ghz 1Gig Ram

Windows XP Home Edition
SP2

X86 Based Pc

C:\ Drive (Windows Drive) 
File System: NTFS
Free Space 30.6 gb
Total Size 37.2 gb

SEA_DISK (D:\) (The Drive I Use For Most of my Programs)
File System: FAT32
Free Space: 96.1 GB
Total Size: 149 GB

Which One of these should i paration and in what format?

---

### Post by ebutton on 2006-10-16
Welcome!

Are you going to dual boot?  If not, then just go slow and read everything.
Do you have a way to get back to this forum with a different computer?  That should greatly reduce your "fear factor".  The people here are wonderful.

Make that wonderful!

Regards,
EdB

---

### Post by UltraM4n on 2006-10-16
I Was Thinking Of Duel Booting Because i already have Windows XP and i do not want to remove it.  and yes i have another computer (well my dads)

---

### Post by Ambimom on 2006-10-16
This is a nice video that explains installation.  Don't be confused by the silly little dramatic sequence that opens the video. About five minutes into it, it shows you how to install.

[http://www.adventuresinlinux.tv/main/component/option,com_frontpage/Itemid,1/](http://www.adventuresinlinux.tv/main/component/option,com_frontpage/Itemid,1/)

Also check out these podcasts on installing for the first time.
[http://www.linuxreality.com/podcast/episode-19-ubuntu-linux-606-part-1/](http://www.linuxreality.com/podcast/episode-19-ubuntu-linux-606-part-1/)
[http://www.linuxreality.com/podcast/episode-20-ubuntu-606-part-2/](http://www.linuxreality.com/podcast/episode-20-ubuntu-606-part-2/)

After you install, try [www.getautomatix.com/](www.getautomatix.com/) [It will save you hours of finding things you need.]

Good luck.

---

### Post by emarkay on 2006-10-16
I have a dual boot setup that works fine - I even modified Grub to lower the timeout and to change the default order.  Look at those links and Google for "Ubunu dual boot" and go for it!

---

### Post by UltraM4n on 2006-10-16
Ok they really didn't talk about parting....they just said ok so you need to squueze the windows part together...and then they said its done!...so...does Ubuntu automatilcy make these parations? Or is there any other thing i need to do before running the installer?

---

### Post by TheWizzard on 2006-10-17
> **UltraM4n said:**
> Ok they really didn't talk about parting....they just said ok so you need to squueze the windows part together...and then they said its done!...so...does Ubuntu automatilcy make these parations? Or is there any other thing i need to do before running the installer?

the easiest way (for windows users) is to boot windows, free space, and use a program like partition magic to reduce the windows partition. 
then boot the ubuntu life-cd and use the free space on your hdd to make a linux partition.

---

### Post by Ambimom on 2006-10-17
Ubuntu will partition during install.  There are three options.  The first one is to erase your hard drive completely...DON'T SELECT THAT ONE!

The next option is to let Ubuntu partition for you.

The last option is for you to select the partitions (but this is not for noobs).

If you have a second hard drive you want to use as your linux system, then you recognize appropriate drive by its size (because the identification is no longer "C" or "d" but "hda" or "hdb". 

The good news is that at every step of the installation, whether on partition or second hard drive. Ubuntu will ask you if you want to proceed.  You can stop and start over.  

It's scary. I know. If you take it slow; and read everything very carefully, you'll be alright. If you're unsure, then stop and start over, until you're more confident.

---

### Post by RRS on 2006-10-17
Do you plan to install Knoppix or Ubuntu? Or maybe another distro?

While installation may vary, the basic partitioning is the same.

[Aysui's site]("http://www.psychocats.net/ubuntu/index.php") has a good [partition info]("http://www.psychocats.net/ubuntu/partitioning") page along with a wealth of other info. [This page]("http://www.psychocats.net/ubuntu/installing") has a good tutorial on installing Ubuntu from the desktop(live) CD.

To install Ubuntu from the "alternate" CD follow the directions on [Herman's site]("http://users.bigpond.net.au/hermanzone/index.htm"), also a good source of other post installation tips.

Your computer specs are more then adequate to run Linux and the C drive has plenty of free space.

As a safety precaution defrag (2 or 3 times) and backup any important data to your D drive before installing "just in case". You might also want to unplug D.

Linux can read/write to fat32 so you're allready ahead of the game for setting up a partition to share data between windows and linux.

Good luck and have fun :)

---

### Post by emarkay on 2006-10-17
I have 2 HDU's and 7 partitions, so I was very paranoid.  I got it right the first time but then decided to modify it (silly me) and took a bit of time to get it back, but I NEVER lost any data.

The partition tools on the Ubuntu CD are great.  I also found a free windows partition tool (there are very few free ones out there - I am not in Windows now so I don't recall its name) to verify and test that all was fine "over there".

What I ended up with was an entire 40Gb partition on HDU 1 for Linux, and it's been no prob switching between the two on boot up.  I also have one small volume mounted in Linux on my desktop where I store files to transfer between Linux and Windows.

---

### Post by UltraM4n on 2006-10-17
Awesome! Alright....
The last option is for you to select the partitions (but this is not for noobs).

If you have a second hard drive you want to use as your linux system, then you recognize appropriate drive by its size (because the identification is no longer "C" or "d" but "hda" or "hdb".

Does that mean by the size i will have to find out what the total size of my external hd is or how much space it has left?

Hold on i'm gonna boot into knoppix live! to see what it said my external was (like hda1 and such)

Ok it showed a USB icon and it was a sda1....

My external HD is a USB one. 149 gigs without data...i have about 95.7 gigs left.its a Sea Gate

---

### Post by Ambimom on 2006-10-17
> Does that mean by the size i will have to find out what the total size of my external hd is or how much space it has left?

What I meant is that you can determine what drive is what, by the size, not the label. When I first installed ubuntu, I was only familiar with the Windows labels of "C" and "D" to identify my hard drives. The way I determined the one on which to install Ubuntu was by it's total size.  

> Hold on i'm gonna boot into knoppix live! to see what it said my external was (like hda1 and such)

That's how linux labels drives. 

> Ok it showed a USB icon and it was a sda1....
My external HD is a USB one. 149 gigs without data...i have about 95.7 gigs left.its a Sea Gate

I think booting to an external drive is possible, but I'm really not sure it's possible.  Check the forums here for instructions on how to install to an external.

---

### Post by UltraM4n on 2006-10-17
Ok i'm not going to install it on my external because of these horror stories.....I'm Going to take the plunge! hopefully i will be messing you from Ubuntu! Thanks For All the Help!

*Adds another reason why linux is better*

---

### Post by UltraM4n on 2006-10-17
Ok i'm messging from the ubuntu live CD and am at the last state of installing
Language: English
Keyboard layout: us
Name: *****
Login name: ******
Location: America/Indiana/Vevay
Partitioning:
  If you continue, the changes listed below will be written to the disks.
  Otherwise, you will be able to make further changes manually.

  WARNING: This will destroy all data on any partitions you have removed as
  well as on the partitions that are going to be formatted.

  The following partitions are going to be formatted:
     partition #2 of /dev/hda as ext3
     partition #5 of /dev/hda as swap

does that mean its gonna delete my windows paration?!

---

### Post by Ambimom on 2006-10-17
Before it does anything, it will ask your permission to proceed.  If you're unsure, then start again. 
 
[I hope you've already backed up your windows drive just in case; and defragged a few times to make sure your partitions are cleanly done.] 


Good luck.

---

### Post by UltraM4n on 2006-10-17
YES! Everything worked PERFECTLY!

Also when i boot into windows again it wants to check for disk concsenty... should i let it do so or no?

Thank You SO MUCH! I Now LOVE LINUX!

---

### Post by Ambimom on 2006-10-17
When you boot, it will ask you which operating system to select.  

I don't know what you mean. Disk content? or Disk consent?

---

### Post by UltraM4n on 2006-10-17
ah i ment Constancy 

like its a blue screen and it says 

Windows Needs To Check C:\ for Constancy Hit Any Key To Stop.

---

### Post by Ambimom on 2006-10-17
Ultraman, I never heard of a check for constancy in windows but there is a check for consistency.

[http://support.microsoft.com/kb/167704/EN-US/](http://support.microsoft.com/kb/167704/EN-US/)

---

### Post by joff13 on 2006-10-17
> **UltraM4n said:**
> H

C:\ Drive (Windows Drive) 
File System: NTFS
Free Space 30.6 gb
Total Size 37.2 gb

SEA_DISK (D:\) (The Drive I Use For Most of my Programs)
File System: FAT32
Free Space: 96.1 GB
Total Size: 149 GB



if to install linux, for you, 150GB of disk are enough I'll suggest to leave C:\ as it's now, backup your data in d:\ (perhaps moving this into C:\)

and than install linux in the old D: partition using the tool you'll get during the installation.

I think D: is hda2 so you'll have something like:

hda2 extended
hda5 /boot ->about 2*RAM
hda6 /swap ->about 256M
hda7 /     ->depend on what you need
hda8 /home ->the rest

enjoy

---

### Post by UltraM4n on 2006-10-18
> **joff13 said:**
> if to install linux, for you, 150GB of disk are enough I'll suggest to leave C:\ as it's now, backup your data in d:\ (perhaps moving this into C:\)

and than install linux in the old D: partition using the tool you'll get during the installation.

I think D: is hda2 so you'll have something like:

hda2 extended
hda5 /boot ->about 2*RAM
hda6 /swap ->about 256M
hda7 /     ->depend on what you need
hda8 /home ->the rest

enjoy
Uh I Already had it installed...

And yes to the other guy thats what i ment (i suck at spelling)

---

