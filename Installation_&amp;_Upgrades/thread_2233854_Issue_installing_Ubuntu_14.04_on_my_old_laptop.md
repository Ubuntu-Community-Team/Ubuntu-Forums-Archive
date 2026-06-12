---
title: "Issue installing Ubuntu 14.04 on my old laptop"
date: 2014-07-11
forum: Installation &amp; Upgrades
---

### Post by gigi3 on 2014-07-11
Hi all, I'm new here. I've just tried to install Ubuntu Desktop 14.04 on my old laptop but with no success. The liveDVD works well, I've explored some features and functionalities if Ubuntu successfully and the laptop is also correctly connected to the Internet by WiFi connection. The problem is that when I launch the installation the system, after the step showing the partition of the HDD and clicking Continue, stop all activity (both on the HDD and the DVD drive, leds off) and seems to do nothing. I waited almost half an hour but nothing happened. At this point I can minimize the install window and interact with the system as normal so it is not freezed.
My laptop is an Acer Travelmate 2420, 1GB RAM, 60GB HDD with, I suppose, two partitions in Windows XP Home SP3 (C and D), Phoenix Bios 1.02.
Thanks in advance and regards.
Gigi

PS: same issue with Linux Mint 17 ...

---

### Post by coffeecat on 2014-07-11
Welcome to the forum!

A couple of questions. When you say:

[quote=gigi3] The problem is that when I launch the installation the system, after the step showing the partition of the HDD and clicking Continue, stop all activity (both on the HDD and the DVD drive, leds off) and seems to do nothing.[/quote]

Which of the choices offered have you selected? There will be something like install alongside Windows, use whole hard drive and "something else" - I can't remember the exact workding of the first two.

Long shot this, but there might be a (fixable) problem with your hard drive partition table which is stopping the partitioner from working. The best way of seeing if this is so is the output of a terminal command. From the Ubuntu live desktop, ctrl-alt-t to open a terminal and then run this command:

```
sudo fdisk -l
```

You can copy the output of the command by highlighting it with the mouse, right-click -> copy, and then pasting it into your post or into a text editor. Please enclose your output between [noparse]```
 and 
```[/noparse] tags to preserve formatting. Simply type out the code tags either end of your output or use the paperclip icon in the toolbar of the advanced message editor.

---

### Post by gigi3 on 2014-07-11
Thanks for the quick reply. I've choosed the 'install alongside windows XP ...' option because I want to keep Windows. Tonight I'll do the test you suggest, thanks.

---

### Post by coffeecat on 2014-07-11
I've subscribed to this thread so I'll see when you post. A couple more thoughts for you.

The fact that you are getting a usable live desktop suggests that the original ISO and the DVD are OK, but it might be worth doing integrity checks if you haven't already. Check the md5sum on the downloaded ISO:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

A link to the Ubuntu ISO md5sums is on that page.

And to check that the DVD was burnt OK, start booting it and as soon as you see the purple screen with two icons at the bottom of the page, a stick figure and a keyboard, tap the space bar to get the old-style text menu. About third on the list is a disc check. Run that. You can check the md5sum of the Mint ISO but you'll have to find the md5sum somewhere on the Mint website. I don't know whether you can do a disk check on the Mint DVD the same, but if you can I should imagine the initial screen is green rather than purple!

The other thing is that if you are wanting to do a dual-boot with Windows, and you can't get the partitioning stage of the installer to co-operate, the other thing you could try is to set up your partitions with gparted from the live desktop first, and then select "something else" at the partitioning page of the installer. You can set up partitions in something else, but I much prefer to use gparted. You have more flexibility with both number and size of partitions than leaving the installer to set up a dual boot for you. If you need help with that, the information from fdisk will tell us all we need to know.

---

### Post by gigi3 on 2014-07-11
I've already tested the integrity of both the iso images (Ubuntu and Mint) but in Windows with [this]("http://www.etree.org/md5com.html") tool and before burning the DVDs. They was both ok. I'll do the DVD check with the old-style text menu at boot time as you suggest. Thanks again.

---

### Post by yancek on 2014-07-11
> Thanks for the quick reply. I've choosed the 'install alongside windows XP ...' option because I want to keep Windows

The Something Else option will allow you to do that.  The Install Alongside is pretty much an auto-install, the user doesn't have much input and it's 'hope for the best'.  Using 'Something Else', would give you much more control over the installation but if you are totally unfamiliar with installing Ubuntu/Linux, you would need to read some tutorial before beginning or you could run into problems.  The link below has an excellent, detailed tutorial as well as some background information on partitioning, etc. and would be useful to bookmark:
 
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by gigi3 on 2014-07-11
Hello, I'm back ...
The `Check disc for defects` give me `no errors found` :p then the `sudo fdisk -l` give me the following:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x34fe34fd
Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     6554519     3277228+  12  Compaq diagnostics
/dev/sda2   *     6554520    60597179    27021330    c  W95 FAT32 (LBA)
/dev/sda3        60597180   117194174    28298497+   c  W95 FAT32 (LBA)
```

In Windows I got C drive 25.7GB total, 12.3 available and D drive 26.9GB total, 10.3 available.
Thanks yancek for the link to those fantastic tutorials, I've just started to read some of them.
Now I'm not sure how to proceed in order to set up the partitions. My intention is to install Ubuntu in a dual boot system togheter with Windows XP, still leaving a little amount of the available disc space to Windows. But, at this time, I don't want to go too deeply ... I cannot wait to have a fresh new Linux system to try ;).
Anyway, I look forward to your advice before proceed ...

---

### Post by yancek on 2014-07-11
You have three partitions which take up the entire drive.  I don't believe xp has any software to resize(shrink) partitions.  You can use the GParted partition manager which is on the Ubuntu installation medium so boot that, when you get to the Desktop click on the Dash (the Ubuntu icon in the upper left) and type:  gparted in the Search box, hit Enter.  The link I posted has a section on using GParted which is very brief but there is a link in that section to a detailed tutorial on gparted.   Review that to learn how to shrink a partition.  GParted will show which drive is largest and which has the most data on it.

---

### Post by sports fan Matt on 2014-07-11
I have a similar speced laptop (Intel pentium M, 992 MB) and was thinking could Xubuntu be a suitable replacement if Ubuntu fails for this indiviual?

---

### Post by coffeecat on 2014-07-12
> **gigi3 said:**
> `sudo fdisk -l` give me the following:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x34fe34fd
Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     6554519     3277228+  12  Compaq diagnostics
/dev/sda2   *     6554520    60597179    27021330    c  W95 FAT32 (LBA)
/dev/sda3        60597180   117194174    28298497+   c  W95 FAT32 (LBA)
```

In Windows I got C drive 25.7GB total, 12.3 available and D drive 26.9GB total, 10.3 available.

It's fairly easy to calculate the partition sizes from the output of fdisk, and this is what they come out with:

sda1 - 3.13 GiB
sda2 - 25.77 GiB
sda3 - 26.99 GiB

First comment - GiB = gibibytes and that is what Windows is showing you the sizes of C: and D: in. It's probably referring to gibibytes as GB, but that is strictly wrong. There's a lot of confusion, but GB should refer to gigabytes, 1 gigabyte = 1,000,000,000 bytes, and GiB to gibibytes, 1 Gibibyte = 1073741824 (1024 x 1024 x 1024) bytes. Some computer traditionalists get upset by the distinction and insist that a gigabyte is 1073741824 bytes. Well - whether or not they have a point, there is enough to confuse one in this. Your hard drive is 60GB (gigabytes) which is equivalent to the 55.89 GiB that the figures I give for sda1+sda2+sda3 come to.

Clear as mud, isn't it? :)

Anyway, the important thing is that sda2 is your C: drive and sda3 your D:, and you need to leave sda1 alone. By the way, we don't use the C:/D:/etc convention in Linux - it's a Microsoft weirdness, and a source of more confusion by referring to partitions as drives. In Linux land, a drive is your physical drive, whether hard drive, flash drive, etc. A partition is a partition, and a drive can have several partitions.

What I would do in your situation is to copy the approx 16 GiB of data in the D: drive to backup media so that I could delete sda3 completely. You could shrink sda3 to the right so that there is space between sda2 and sda3, but that would take many hours, and it would be easier and quicker, and less prone to problems, to completely clear the space to the right of sda2, and reconstruct your partition layout afresh.

I would then shrink sda2, using Gparted as yancek says, down to no less than 20 GiB. Windows needs room to breathe, and it is currently occupying about 13-14 GiB of that partition according to the figures you give. Windows XP has no inbuilt tool to resize its C: partition so you have to use Gparted. 

So, say sda2 is now about 20GiB, and with sda1 occupying 3 GiB, you would have about 32-33 GiB of contiguous unallocated space to create partitions for Ubuntu and a data partition. I would suggest the following, and these are only my suggestions - there are other ways to proceed:

Use Gparted to create an extended partition - you need this - you need at least three more partitions and your limit for primaries is 4. Your extended partition will probably be sda3. You then create logical partitions in this (Linux can boot from logical partitions, unlike Windows which can't) which will be numbered from 5. I would suggest this:

**swap partition** - 1GB to match your RAM.

**ext4** - to be your Ubuntu root partition. If you want to store 16 GiB in the next partition, you have little breathing space. 15 GiB for this partition would be ideal, but I think you would need to go for 10 GiB. A fresh install of Ubuntu takes up a little less than 4 GiB (if I remember correctly) and it doesn't suffer from the bloat that Windows collects to itself, but you would need to store little if any personal data in your home folder to leave room to install applications. And then...

**ntfs** - the remaining space, about 20-22 GiB if you make your ext4 partition 10 GiB. Store all your personal data on this. Ubuntu can read/write ntfs so a shared ntfs data partition is a good idea with a Windows/Ubuntu dual-boot.

That leaves how to use the "something else" option - if you need help, post back. You have a few things to think about!

---

### Post by gigi3 on 2014-07-12
First of all, many thanks to all of you guys for the precious and quick help and it is rewarding to have to deal with so enthusiastic friends. I'm 50 years old and in fact not completely new to Linux, however my only previous experience with Linux and partitioning was with one of the first SuSE releases on a IBM Thinkpad in 90's ... and I have forgotten almost everything :mad: so, I'm happy to try again and seems that things are much simpler now but I've to re-learn ... so please, give me the time ;).
My first serious doubt now is: I have to really backup my Windows XP system with CloneZilla before manage with disc partition? I know that is up to me how to proceed with this question but I read that this procedure is not simple and sincerely I just want to avoid if possible ... however the main issue is that, as you know, WinXP is no longer supported and I don't know if my inbuilt Acer system recovery will do the job in case of unrecoverable errors with disc partitioning and the very long and annoying Service packs updating process ...
Thanks again, sorry for my poor English and best wishes from Turin, Italy ):P

---

### Post by coffeecat on 2014-07-12
> **gigi3 said:**
> My first serious doubt now is: I have to really backup my Windows XP system with CloneZilla before manage with disc partition?

I would certainly recommend imaging your Windows partition before resizing it. Resizing a partition always has the potential to go wrong. But if you find clonezilla daunting there's a much more user friendly imaging/cloning app for Windows that I have used many times, Macrium Reflect, and it has never let me down - yet! It's not open source - it's proprietary - but you can get a free version here:

[http://www.macrium.com/reflectfree.aspx](http://www.macrium.com/reflectfree.aspx)

The nice irony about it is that the rescue CD for this Windows application which runs in Windows is Linux based. In fact you use the rescue CD to restore your system from a saved image.

---

### Post by gigi3 on 2014-07-12
Just finished to write the System Image with Macrium Reflect subdivided in 3 DVDs. If I understood right this is the only image I need to eventually restore Windows XP. Or do I need to write a Windows PE based Bootable Rescue Media?

[ATTACH=CONFIG]254672[/ATTACH]

---

### Post by coffeecat on 2014-07-12
> **gigi3 said:**
> Just finished to write the System Image with Macrium Reflect subdivided in 3 DVDs. If I understood right this is the only image I need to eventually restore Windows XP. Or do I need to write a Windows PE based Bootable Rescue Media?

[ATTACH=CONFIG]254672[/ATTACH]

If you ever need to restore the image you need to boot up a rescue CD. Coincidentally, I just installed the latest version of Macrium Reflect myself today. I see they now offer the choice between the Linux based rescue CD and a Windows PE based one. The Linux one works just fine if you are going to restore your system, or any partitions you have imaged, to exactly the same start sector and to exactly the same partition size. I see that the Windows PE based restore CD, which is new to me, offers more flexibility. It looks as though it would allow restoring an image to a partition that starts at a different sector or is a different size, although I haven't looked into this closely yet. I suggest you create one or both of the rescue CDs now in case you need it in the future.

---

### Post by gigi3 on 2014-07-12
Sorry for the stupid question ... I haven't read nothing about restoring yet. I don't know how the system restore procedure is implemented but, how and when the rescue CD can be replaced by the 3 DVDs that currently old the system image? May be is better to have the system image in an external USB HDD?

---

### Post by coffeecat on 2014-07-12
If you ever need to restore your system, you boot up with the recovery CD and work from the live environment of the booted CD - a bit like a live Ubuntu session. But one thing has just occurred to me. You say you have created your backup images on DVDs. That means that you would need to boot up the rescue CD in the internal optical drive and use a USB optical drive for the DVDs. If you don't have a USB optical drive, you won't be able to use the DVDs that you have created. There are two other options.

1 - I notice that you can create a bootable Windows PE based USB system from the utility in Macrium Reflect. That would only work if your laptop supports USB booting. If it is above a certain age, it won't and you would have to use option 2.

2 - This is my preferred option. I write my Macrium images to a USB hard drive formatted NTFS. That way I can boot up the rescue CD from the internal drive and the live session can read from the USB drive image and write to the internal hard drive.

To summarise: you need either a second optical drive, or be able to boot from a flash drive, or write your backup images to and store them on a NTFS USB hard drive.

---

### Post by gigi3 on 2014-07-12
My laptop is DVD drive bootable (I've tested Ubuntu LiveDVD in this way) but not USB. I have an external optical DVD drive and an external (Western Digital) USB HDD also but I don't know if the last is an NTFS drive. How may I check this?

---

### Post by coffeecat on 2014-07-12
> **gigi3 said:**
> an external (Western Digital) USB HDD also but I don't know if the last is an NTFS drive. How may I check this?

If you bought it pre-formatted, it's more than likely to be NTFS. It's been a long time since I used Windows XP, but if you plug the drive in and switch it on, the Disk Management Utility should tell you if it is NTFS. You'll soon tell if you try to use it in Macrium Reflect. The older FAT32 filesystem has a maximum filesize of 4GB so either Macrium will error out when your image gets to 4GB or it will refuse to use FAT32 in the first place. 

You can also check the filesystem in the Ubuntu live session. If you plug the drive in and let it be mounted and then run the "sudo fdisk -l" command you used earlier, your WD drive will be identified as sdb (or perhaps sdc) and you will see whether or not it is ntfs from the output.

By the way, I've just noticed something unexpected about your earlier fdisk output. Both your XP C: and D: partitions are FAT32 which is unusual. XP can run from FAT32 but it is a less robust filesystem than NTFS, and has the filesize limitation I mentioned. If you decide to delete the D: partition as I suggested earlier, I recommend replacing it with a NTFS partition, which you can do from Gparted.

---

### Post by gigi3 on 2014-07-12
mmmmm ... just tried to explore the newly created DVDs with my USB DVD external drive (it's a Pioneer DVR-111B). The first and third DVDs are correctly accessible (please see attached figs) but the second give me an error like 'Could not read from the disc. The disc may be damaged or it uses a format not compatible with Windows'. Furthermore, may be I'll have troubles during restoring using so large files (about 4.5GB) on my laptop FAT32 windows partitions? Probably your second option (USB external HDD for the system image) can be considered the safest one ...

[ATTACH=CONFIG]254674[/ATTACH][ATTACH=CONFIG]254675[/ATTACH]

---

### Post by coffeecat on 2014-07-12
Don't confuse the size of the image files of your Macrium backups and the maximum filesize allowed on a FAT32 filesystem. If you create a Macrium image on your external hard drive, it will be about 11GB - that's one large file. But it is a compressed image of a whole system consisting of thousands of small files. If you ever need to restore your system from it, all those constituent smaller files in your C: partition will be recreated from the image. 

The problem you are seeing with disc 2 is to be expected occasionally, unfortunately. Which is another reason why I prefer to make my images on an external hard drive.

---

### Post by gigi3 on 2014-07-12
Last question before making the image on the USB external hard drive. If I click on 'Create an image of the partition(s) required to backup and restore Windows' in Macrium Reflect the dialog automatically select the Partition 2 only, not the 1st (PQSERVICE). Is this because the 1st partition it's an internal system recovery (one of the Acer laptop feature that allow the user to restore the original computer state)? Does this mean that this partition is not necessary to restore the system?

[ATTACH=CONFIG]254678[/ATTACH]

---

### Post by coffeecat on 2014-07-13
I'm not familiar with Acer, but that looks as if it could be a recovery partition which restores the machine to its factory state, that is with XP not updated and without all your applications. Although you said you don't want that, since you have doubts that you could update the now obsolete XP, it wouldn't take long to create an image of that partition. On the Macrium screen previous to the one you posted - as far as I remember - you should be able to select only the first partition. Or perhaps you do it on the screen you posted by unticking the second partition and ticking the first. Whichever it is, you have the choice of imaging just one partition at a time or the whole hard drive.

---

### Post by gigi3 on 2014-07-13
Ok, just finished my backup procedure ... two partitions images, one for the main C: (about 9GB compressed) and another one for the original Acer's recovery partition (named PQSERVICE, about 3GB compressed, just in case). Both stored in the WD Elements ext HDD (checked, it has an preformatted NTFS filesystem). Yesterday's DVDs in the trash ):P. I've also burned a DVD as a Linux Rescue disc (19MB only). Unfortunately, the attempt of making a Windows PE one give me an error (please see attached files), anyway I'll check the integrity (bootability) of the Linux rescue disc and I assume that it is sufficient to have one of these. Now I'm ready to go with the Gparted partitioning. I emptied the Windows D partition as you suggested so I'll create an complete NTFS Linux room here, but I was thinking to left the C windows partition (as well as the empty PQSERVICE one) as is. Its has about 11GB of free space that I would like to left to XP. It is not clear to me why you suggest to shrink the C partition. I mean, does this C partition section needed for Ubuntu?

[ATTACH=CONFIG]254688[/ATTACH]  [ATTACH]254689[/ATTACH]

---

### Post by coffeecat on 2014-07-13
I was only thinking of optimising the space you have to give you a few more GBs in which to install Ubuntu and have a Data partition. But if you did shrink the Windows partition and ever needed to restore it from your Macrium image, you would probably need the Windows PE rescue disc rather than the Linux one. The fact that you had an error creating the Windows PE rescue disc, and you had one dud DVD out of 3 when you created a set of image DVDs, suggests either that you have a faulty set of writeable DVDS or, more probably, the optical drive on your laptop is giving problems. It may just need to be cleaned with one of those optical drive cleaner discs, or maybe it is beginning to fail. Let's hope not, but the laptop does seem to be an old one.

Just something to bear in mind.

---

### Post by gigi3 on 2014-07-14
With respect to the mounting error I got during the WinPE Rescue CD creation, I found [a post]("http://support.macrium.com/topic.asp?TOPIC_ID=4082&SearchTerms=reparse,points") in the Macrium forum that reflect the same situation. The problem seems to be the FAT32 old type Windows partition. This file system type is not supported for creating the WAIK based WinPE rescue CD. It also seems that it is possible to convert a FAT32 fyle system to an NTFS one in Windows with the [Convert.exe]("http://support.microsoft.com/kb/307881") command ... but there is also the option to create a 'Standard' Win PE rescue CD in Macrium Reflect so this will work in FAT32 file systems. I'm inclined to adopt the second solution ... what do you think about this?
A Linux Rescue CD seems to do the job as well ([here]("http://support.macrium.com/topic.asp?TOPIC_ID=4993&SearchTerms=reparse,points"), last reply ...)

---

### Post by coffeecat on 2014-07-14
If you are not going to be resizing the C: partition, then the Linux based rescue CD will be just fine.

---

### Post by mastablasta on 2014-07-14
if you plan to use D: partition for Linux then all you need to do is delete that one and leave it to installer (just select to install to largest free disk space). if you are doing any resizing you need to defragment first. 

you could ocnvert to NTFS - might not be a bad idea. FAT32 has a file size limit and NTFS is stable for a while now. i just recently converted to it.

as for backups if oyu are doing it ot external drive i am not sure why are you using iwndows tools when you can easilly image all parittions with free Linux tools. you can boot using those tools, repair errors, recover partitions etc. 

for a real rescue disc have a look at ultimatebootCD - it has diagnostics, recovery tools etc.

---

### Post by coffeecat on 2014-07-14
@mastablasta, did you read *any* of this thread before you posted?

---

### Post by gigi3 on 2014-07-15
Hi, just partitioned the HDD with Gparted, now it is as follow
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     6554519     3277228+  12  Compaq diagnostics
/dev/sda2   *     6554520    60597179    27021330    c  W95 FAT32 (LBA)
/dev/sda3        60598272   117209087    28305408    5  Extended
/dev/sda5        60600320    62648319     1024000   82  Linux swap / Solaris
/dev/sda6        62650368    83130367    10240000   83  Linux
/dev/sda7        83132416   117209087    17038336    7  HPFS/NTFS/exFAT

```
i started the installation with "something else" option but i stopped the procedure because I have a doubt. In the drive table the partitions are not mounted, I mean they all have empty fields in the mount column. In Gparted I have not considered the mounting steps. The question is, when and where I have to mount the partitions? Furthermore, which partitions have to be mounted? I suppose the sda6 should be the root, along with home but the other one? As you can easily imagine, I want sda6 for Ubuntu and sda7 for common data (WinXP and Linux). Anyway, I already checked the new partitions in WinXP and the sda7 is correctly recognized as NTFS partition (sorry, drive ;))
Gigi

---

### Post by coffeecat on 2014-07-15
I'm having to go from memory here, but this is what you do.

Don't mount any of the partitions - they have to be unmounted for the installer to proceed.

Start the installer and when you get to the partition stage, select something else. Highlight sda6 and there is a button called "change" or something similar. Click on that and a small windows opens. In the first field (I think it's "use as") select ext4. Don't change the size. Tick the format box. It's a freshly formatted partition and you don't need to, but if you don't the installer grumbles at you and I can't remember the sequence of events to get past that. In the last field - I think it's mountpoint - choose the first option in the list - '/'. That stands for root partition.

Don't worry about the swap partition - that is picked up automatically.

As for your NTFS sda7 partition, you can choose a mountpoint now but I would advise doing this manually later. The ntfs mount options that the installer applies are far from optimal and actually cause problems. I filed a bug for this years ago, the bug was comprehensively ignored, and it is still the same all these years later. I gave up in disgust and now content myself with advising people on better mount options for /etc/fstab.

Once you've selected sda6 as /, make sure that grub is being installed to sda - that is the default - and then click on continue and let the installer do its stuff.

Once you have a working dual-boot, you can mount sda7 when needed from nautilus, but if you want it mounted on each boot, post back and I'll take you through what to do. The information is here:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

But if you want help with that, I can talk you through it.

---

### Post by gigi3 on 2014-07-16
Finally, I have a fresh and working Ubuntu system on my little old Acer, now dual boot. Many thanks coffecat for your invaluable realtime support! The only issue I got during the fluent installation process was the disconnection from the WiFi network that occured about three or four time so the installer wasn't able to download the latest updates (mainly libreOffice and Language Support related packages). It's strange because the connection now seem to be very stable, at least during normal usage of the system (e.g. web browsing with Firefox). Next step now, learning mounting.
Anyhow, I got an issue related to the my laptop powering off. In both Shutdown and Restart commands the notebook stop its activity and doesn't power off or reboot. Pressing Ctrl-Alt-Backspace to look at the console messages the last lines looks like:
```
* Deactivating swap ... [OK]
* Unmounting local filesystem ... [OK]
* Will now halt

```
after Shutdown command and
```
* Deactivating swap ... [OK]
* Will now restart

```
after Restart. So to power off the computer completely I have to hold down the on-off button for 4-5 seconds, or disconnect the power source cable (the battery is dead, I don't use it anymore). Same behaviour with the liveCD. May be an hardware problem ...
Gigi

[ATTACH=CONFIG]254759[/ATTACH]

---

### Post by coffeecat on 2014-07-16
I'm glad that you managed to install the system OK. I always decline the latest updates when installing as that always seems to make the process longer than if I update the system in the normal way after installing.

I'm not sure what to suggest about your shutdown problem apart from checking that the system is fully up-to-date. If you want help with the shutdown issue, it would be better to start a new thread with a title mentioning this issue. You will attract more people likely to be able to help with a fresh thread. 

If you do want help with mounting the ntfs partition and that wiki page I linked, post back to this thread. It will remain open until autoclosed in a year and I have it subscribed so I will see if you do decide to post here.

---

### Post by gigi3 on 2014-07-17
Hi, just a question regarding a possible hardware 'upgrade' on my Travelmate ... in case I'll buy a couple of [1GB RAM boards]("http://www.ebay.it/itm/2gb-Kit-Acer-Travelmate-2420-PC2-5300-DDR2-667Mhz-Laptop-Ram-SODIMM-200-Pin-/221337556841?pt=UK_Computing_ComputerComponents_MemoryRAM_JN&hash=item3388bf1769&_uhb=1"). I'll need to change in some way the Linux-swap partition to the new 2GB memory condition? And how, if needed? Thanks

---

### Post by coffeecat on 2014-07-17
You only need to do that if you ever need to hibernate the system to RAM, when the swap must be the same size or larger than RAM. If you are not going to hibernate, 1GB of swap with 2GB of RAM should be fine.  

If you do need to enlarge the swap partition, that is doable but time consuming and with your current layout would require that you shrink your Ubuntu root partition by 1GB. If you do decide to do that, the procedure would be, in brief:

Boot from a live CD/USB. You have to use a live session.
In gparted right-click on the swap partition and choose swapoff.
Shrink the sda6 Ubuntu partition from the left. **This will take a long time**.
Enlarge the swap partition into the space you have freed by shrinking sda6.

As always with partition manipulation, backup anything you don't want to lose.

If that was my setup, I wouldn't bother. I would simply avoid hibernating the system.

---

### Post by gigi3 on 2014-07-23
Hi coffeecat, I have a second HDD to play with ... it's identical to the first one (60GB) I used recently to successfully install Ubuntu 14.04 along side with Windows XP. It comes from another even older Acer laptop (Aspire 1360, with broken DVD drive and only 512MB of RAM) that I don't want to keep alive any more. This second HDD has the same Windows XP structure with C and D partitions as the first one but in this case I'd like to use it entirely with Linux. I was thinking to install the lighter Ubuntu flavour available that should be Lubuntu, in order to my laptop hardware as 'faster' as possible. So, the question. I was wondering if can you help me in deciding an optimal partitioning strategy. As for the previous HDD, it is intended for 'general use', I mean Linux learning and testing. How many partitions should be considered and which type? I was wondering if three/four partitions like swap, root, home (/usr, /usr/local?) can be sufficient and useful. Do I need a boot partition?
Cheers

---

### Post by coffeecat on 2014-07-23
Since you are wanting advice for a good partition layout for Ubuntu or Lubuntu by itself on a 60GB drive, It would be best to start a new thread. This one is now over 30 posts long and started with your need to install Ubuntu as a dual boot with Windows and have a shared data partition. It would be useful to you to have different opinions and you are more likely to get more people attracted to a new thread than an older one with many posts. But I will offer a few personal thoughts to get you going.

As a bare minimum you need swap and root. There are pros and cons to having a separate home partition or a separate data partition with home kept in the root partition. My preference has always been for a separate data partition but others prefer a separate home and it would be useful for you to hear reasons for both in order for you to make up your own mind. 

One thing I do suggest is don't have a separate boot partition. They cause more problems than they solve and the problems they are designed to solve are mostly in the past. Almost daily I see a "help, my boot partition is full" thread, and I always wonder why they chose a separate boot partition in the first place. There was once a BIOS limitation that didn't allow booting from boot files physically located beyond a certain point (I cannot remember how much) from the beginning of the hard drive, and a boot partition as the first partition was a way of avoiding that problem. That was years ago, though, and unless your machine is ancient is unlikely to be a problem.

Lastly, don't follow what you might come across where people have set up separate /var, /usr and goodness-knows-what partitions. For a home setup that is simply weird.

---

