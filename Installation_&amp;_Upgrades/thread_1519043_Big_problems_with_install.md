---
title: "Big problems with install"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by NameUnknown on 2010-06-27
Okay, so I was going to install Ubuntu 10.4 and use it as my main OS while running Windows in VMs.  I've run into a problem though, apparently there is no easy way to install Ubuntu onto FakeRAID.  My systems specs are below.  


AMD Phenom II 1090T w/Prolimatech Megahalem
8GB G.Skill DDR3 1333
Gigabyte GA-89FXA-UD5
ATI HD5970 (maybe a second later)
BFG Ageia PhysX
2x G.Skill Falcon 64GB SSD (RAID 0)
1x WD Caviar Black 640GB
Corsair HX1000W PSU
CM HAF932 (fan modded)

I'm trying to get it to install onto the SSD RAID made using the SB850 (southbridge) as the raid controller.  The problem though is that when I do so it fails each time.  I found the instructions for how to install using FakeRAID [here]("http://ubuntuforums.org/showthread.php?t=1360445").  THese got me far further along, but when I get to 
> 5. Login into the installation
**sudo chroot /mnt/root /bin/bash**It says that there is no such file or directory???  Does anyone know what is going on or how to resolve this?

I also had a thread on another forum, but I figured I would ask here, below is the previous thread, I have removed the names of forum members for their sake.  As you can see they helped me along to this point through other issues, but now I am stuck again.  

I like linux, it just never installs easily for me.  This install, as well as for my P4, went terribly, but once installed was great.  So any help would be appreciated.


[QUOTE=ME]Does Ubuntu not have native support for installing onto a SATA SSD RAID 0 Array?  Every time I boot the disc to install it says there is an error and its loading a live session to help figure it out.  Its not in AHCI mode, its in SATA Type mode for the array.  Anyone know if support is the culprit or not?[/QUOTE]

> I also had issues when i tried to install kubuntu on my velociraptor raid 0 array. never did find a solution.[QUOTE=ME]someone has to know, its got to be out there, but Im leaving for the weekend so I dont have a lot of time as im still packing up :p[/QUOTE]

[QUOTE=ME]To be specific, the error window says:

The installer encountered an unrecoverable error.  A desktop session will now be run so that you may investigate the problem or try installing again.[/QUOTE]

> have you tried the alternate disk?

it is supposed to work in sticky situations, but it didn't for me. :-([QUOTE=ME]the alternate disk??????


When i tried installing from the live session I get as far as installing, then it throws an error saying:

The ext4 file system creation in partition #1 of Serial ATA RAID pdc_ceigefbfi (stripe) failed.


Also, when I run gparted from the live session, it doesnt see the array, but from a Gparted CD it does.[/QUOTE]

> alternate install:

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate)[QUOTE=ME]dont have time to do that now, just tried remaking the partitions already as ext4 partitions, its a no go.  Its like it cant do anything to the raid since its a raid.......

EDIT:   Is [this]("https://help.ubuntu.com/community/FakeRaidHowto") the problem?[/QUOTE]

> sounds like it tbh. 

this is again another example of open source choices here, albeit it is annoying one, but you will learn to appreciate the choice in the long run. :)> I think Linux only supports software RAIDs> it supports software and hardware raids, if it didn't, then it wouldn't have a good statue in the server community as it has...

its been a few years since i've installed any form of linux on a raid of any type, but at the time i had a  raid card when i did it, so i am betting the onboard raid isn't really raid, but a fakeraid like the article he posted mentioned.

one of the reasons why i don't use raid, even tho my board is capable of it.> I remember trying to install Ubuntu 9.10 on FakeRAID back when 9.10 was the latest Ubuntu. There was a huge bug with dmraid, so that my drives would show up as not being a part of the RAID in the Intel RAID manager before I cold rebooted my computer. But the version before that worked completely fine, albeit I had to use the alternate install CD. The latest Ubuntu CD's do not require the alternate CD install, as far as I am concerned.[QUOTE=ME]So, I guess what I am hearing is that I need a real RAID card to do this with Ubuntu or any other linux?[/QUOTE]

> I don't think that's what you're being told at all. Certainly a real hardware raid is superior to a software raid but Linux should have no fundamental problem with either.  Assuming you now have v10.04 it should apparently just work.  If it doesn't you may need the alternate iso. My guess is you need a proper initrd (initial ramdisk) file which loads essential drivers earlier than a kernel with the driver configured as a loadable module or instead of a "built in".

In order to mount the root filesystem the booting kernel through one or the other devices needs to load raid support early.  This should be commonly addressed on Ubuntu forums but if you wait till someone else here that uses raid signs on, more specific help will come here too.[QUOTE=ME]How would I go about making such a file or acquiring one?

As for following the steps [HERE]("http://ubuntuforums.org/showthread.php?t=1360445"), When I try to mount the partition using ```
sudo mount /dev/mapper/pdc_ceigefbfi1 /mnt/root
```It says that I need to specify the filesystem type.  The partition though is already formatted in NTFS.  I had done this earlier with ext4 and it said the same thing.

EDIT:  Looks like I was actually attempting to mount the swap space......[/QUOTE]

> just add "ntfs" to the end of that line. you have to tell it what it is formatted as.[QUOTE=ME]i was trying to mount swap space /facepalm

using the installer in the live session I get to prepare disk space, and i can only use **Erase and use the entire disk** to select the raid array, otherwise it targets my 640.  I did it that way, got all the way to the install stage, i told it to put the boot record on the array, and it gave me an error with no text, just two sets of 3 question marks.

I hate to say it but so far im 0/2 on easy Linux installs :(  But every time I get it up and running I like it.[/QUOTE]

---

### Post by darkod on 2010-06-27
In the middle of that, when you said you "don't have time to do that now", did you mean trying the alternate install cd?
You need to use the alternate install cd for RAID and/or LVM. It might help you, I don't know why you insist on the standard cd.

Another thing, since you plan to have only ubuntu (windows in VM), you can also use software raid which seems to work better than fakeraid. But for raid0 you need to make a /boot partition outside the array, that's the limitation. For raid0 it has to have /boot partition outside the array.

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by NameUnknown on 2010-06-27
When I said I didn't have time, it was about the alternate CD which I have downloading now.  I left about 10-15 minutes later to go camping for a couple nights.  Thats why I have been using the standard disc.  The atlernates torrent is showing about 40 minutes left.
I had been hoping that using those instructions I would be able to get it to work, but I guess I am going to have to wait for the alternate disc to finish.

I didn't want to use a software Raid because I do want a partition that I can use for certain programs and benchmarking for other forums.

---

### Post by darkod on 2010-06-27
I don't have much experience with raid, but in my humble opinion the instructions you linked don't help much. At first glance, that is only instructions how to remove grub2 and install grub1.

But I haven't heard that grub2 is a problem with fakeraid itself. One reason why people might think the instructions helped them, is if they insisted using the liveCD. It's no secret the liveCD doesn't install grub1/grub2 correctly to fakeraid, that's why they recommend to use the alternate cd. And then those instructions helped them install grub1 and it worked. But most probably grub2 would have worked too only if the alternate cd was used.

In other words a lot of fuss and terminal commands when it would have worked with the alternate cd in the first case.

Of course, sometimes it won't work installing fakeraid even with the alternate cd. But lets see what happens on your system with using the alternate cd and then decide what to do.

---

### Post by NameUnknown on 2010-06-27
So Do I need to make a partition on the HDD to make a /boot mounting point since I am partitioning the SSDs?  BTW Im in the Alternate Install Disc now

---

### Post by NameUnknown on 2010-06-27
Well, I guess it went further.  It is now saying:

The attempt to mount a file system with type ext2 in Serial ATA RAID pdc_ceigefbfi1 (partition #1) at / failed.
You may resume partitioning from the the partitioning menu.
Do you want to Resume Partitioning?

So my question, where do I make the mount point?  It seems that is what is holding me up now.
Also, how do I use ext4?  I formatted ext4 initially and it failed to format the partition.

---

### Post by ronparent on 2010-06-27
darkrod offers excellent and very practical advise. I looked at your reference for installing the desktop version and based on my experience found it a bit contorted. I have successfully installed 10.04 to a raid0. 

First off you should be made aware that I have found gparted run from 10.04 useless to create or partition raid arrays. In my case I pre-partitioned the raid drive using gparted from a 9.04 install. Installing dmraid to any earlier version live cd would serve the same purpose. Note, that you will not be partitioning to to unallocated space in sda, sdb, etc. but to unallocated space within the symbolic link titled to a name like nvidia_abcdefghi or sil_abcdefghi etc. This will appear once your raid bios is set up. Write it down because you will habe to select this later as the location to install grub to (if you intend to boot from the raid0 array)

Once the partition structure you want to install to is present in your raid0 I found that the install proceeded normally by selecting to manually partition and then selecting the target partition you created to install to. If you intend to boot to your ssd array, in step 8 of the install process you will click on the advanced button on the screen to manually enter the symbolic link of the raid0 to install the grub2 MBR to. Although I admit that things can go wrong, in my case everything worked as planned when I rebooted. If you plan to try this route I will follow this thread to help where I can. Otherwise darkrod can help you.):P

---

### Post by darkod on 2010-06-27
> **NameUnknown said:**
> So Do I need to make a partition on the HDD to make a /boot mounting point since I am partitioning the SSDs?  BTW Im in the Alternate Install Disc now

As I said, my knowledge of raid is limited, but as far as I know, the separate /boot I was talking about is needed for software raid0, not fakeraid. Did you change your mind and want to use software raid now? For that purpose, you would need to disable your BIOS raid setting, and treat the disks as two separate. The raid0 is on OS level.

If you are still trying with fakeraid, upon booting the alternate cd it should detect the raid0 and offer to activate it. Once it does, I suggest to delete all previous partitions (if they exist) and start clean.
You will need to create / and swap, not sure if you planned other partitions like separate /home. You simply create them onto the raid device which should be shown as single device because of the active fakeraid.

---

### Post by NameUnknown on 2010-06-27
So you did via terminal?  because right now I am in the alternate CD, and it wont mount the filesystem (ext2).  If I try to change the mount point from  /  to anything else it says no root file system.  If I try to format in ext3/4 it fails to format.  So if you did it via terminal, Ive got other issues to fix as well....

---

### Post by NameUnknown on 2010-06-27
> **darkod said:**
> As I said, my knowledge of raid is limited, but as far as I know, the separate /boot I was talking about is needed for software raid0, not fakeraid. Did you change your mind and want to use software raid now? For that purpose, you would need to disable your BIOS raid setting, and treat the disks as two separate. The raid0 is on OS level.

If you are still trying with fakeraid, upon booting the alternate cd it should detect the raid0 and offer to activate it. Once it does, I suggest to delete all previous partitions (if they exist) and start clean.
You will need to create / and swap, not sure if you planned other partitions like separate /home. You simply create them onto the raid device which should be shown as single device because of the active fakeraid.
That is exactly how it is setup, new swap, new /, and an extra for Win7.  But it cannot mount the main partition at /

---

### Post by darkod on 2010-06-27
> **NameUnknown said:**
> That is exactly how it is setup, new swap, new /, and an extra for Win7.  But it cannot mount the main partition at /

Did you create them right now with the alternate installer or had them created in advance?

---

### Post by NameUnknown on 2010-06-27
At first I had created them with a GParted disc, that setup failed, so I removed them all and remade new partitions, which again failed.  I just went through it again and took pictures to show you what is going on.  Here are the first 5 pics of it, the other three are in the next post.

---

### Post by NameUnknown on 2010-06-27
Here are the other three pictures

---

### Post by darkod on 2010-06-27
I agree, it should have worked. Just out of interest, what will happen if you start again, delete all current partitions, and create new ones but this time make the / ext4. Not that it should matter.
Did you plan to use ext2, not 3 or 4?

---

### Post by NameUnknown on 2010-06-27
Using ext4 fails to format, its just plain weird.

---

### Post by darkod on 2010-06-27
I'm running out of ideas. :(

I would try software raid, just to see if it works if nothing else. In software raid you can also have partitions if that's stopping you. In fact, you create mirror partitions on both disks and mark them as Software RAID members. Then with Configure Software RAID you pair them up and set the level (0). Note that with this approach you do need /boot outside the array, it can't boot from software raid0 if it's inside.

---

### Post by NameUnknown on 2010-06-27
I'll try that tonight,Im going to continue to fiddle with fakeRAID as I would prefer to have the SSD's raided for Win7 as well.  I may end up just running one SSD per OS even though I dont need all 64GB for Win7

---

### Post by NameUnknown on 2010-06-29
Okay, so I can't get it to work.  So now the question becomes this:

If I do a software RAID will all VMs already be RAIDed, or will each one need to have its own softRAID setup?

---

### Post by darkod on 2010-06-29
> **NameUnknown said:**
> Okay, so I can't get it to work.  So now the question becomes this:

If I do a software RAID will all VMs already be RAIDed, or will each one need to have its own softRAID setup?

I guess it depends how are you doing your VMs, but softraid wouldn't be much different than fakeraid. For the OS it's still a single device, for example single root partition.

If you install lets say VirtualBox, it doesn't know anything about the softraid. It sees root and installs.

---

