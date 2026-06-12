---
title: "Partition"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by kevb8ll on 2011-03-04
Hi

I am installing 10.10 on my PC. I have changed the hardware and the previous install was for a x64 I now have x32.

I ran the live disk and have selected install.

I am now on the partition page, (manual). I am happy with the concept of partitioning and which partition is which, but I can only change the linux partition.

At the moment I have @60G NTFS, 1G swap and @18G Linux. I want to reduce linux partition to about 12G (which is fine I've done that) I now have free space. I want to increase the swap partition to 2G and the remainder to be added to the NTFS partition.

However, I can't add any more disk space to the latter partitions. The Swap partition has the space bar available, but the increase is greyed out and on the NTFS partition, there is no option at all.

Can anyone help? Did I miss something?

Kev

---

### Post by mikewhatever on 2011-03-04
It's hard to tell if you missed something without actually seeing the layout. The swap partition might simply be in use and you need to turn it off with the **sudo swapoff** command. The ntfs partition probably has no free space to expand too.
In short, if the above helps you, fine, and if not, post a screenshot of Gparted, or the output of **sudo fdisk -l**.

---

### Post by kevb8ll on 2011-03-04
> **mikewhatever said:**
> It's hard to tell if you missed something without actually seeing the layout. The swap partition might simply be in use and you need to turn it off with the **sudo swapoff** command.

Should I do that after running the Live Disk before selecting installation?


> **mikewhatever said:**
> The ntfs partition probably has no free space to expand too.

I don't think that's it, there is about 4G not assigned to a partition. 

> **mikewhatever said:**
> In short, if the above helps you, fine, and if not, post a screenshot of Gparted, or the output of **sudo fdisk -l**.

Ok will do, thanks for your advice.

---

### Post by kevb8ll on 2011-03-04
Ok here the images:

[[IMG]http://i6.photobucket.com/albums/y219/kevb8ll/th_Screenshot1.png[/IMG]](http://s6.photobucket.com/albums/y219/kevb8ll/?action=view&current=Screenshot1.png)

The initial screen.

[[IMG]http://i6.photobucket.com/albums/y219/kevb8ll/th_Screenshot2.png[/IMG]](http://s6.photobucket.com/albums/y219/kevb8ll/?action=view&current=Screenshot2.png)

Showing the Swap and existing Linux partitions.

[[IMG]http://i6.photobucket.com/albums/y219/kevb8ll/th_Screenshot3.png[/IMG]](http://s6.photobucket.com/albums/y219/kevb8ll/?action=view&current=Screenshot3.png)

I selected the swap partition and as you can see, the up arrow is greyed out. (I ran the sudo swapoff -a command before.

[[IMG]http://i6.photobucket.com/albums/y219/kevb8ll/th_Screenshot4.png[/IMG]](http://s6.photobucket.com/albums/y219/kevb8ll/?action=view&current=Screenshot4.png)

This final image, shows the NTFS partition selected. Here you can see there is no option to increase it's size.

Basically I want to add 1G to the swap and the rest to NTFS.

Over to you!

---

### Post by mikewhatever on 2011-03-04
You have the ntfs partition, then the swap partition, then the Linux partition, and then some unallocated space, which is nowhere near the ntfs partition. As said above, the ntfs partition has nowhere to expand, and you'll have to move sda5 and sda6 out of the way first, before expanding sda1.

---

### Post by kevb8ll on 2011-03-04
> **mikewhatever said:**
> You have the ntfs partition, then the swap partition, then the Linux partition, and then some unallocated space, which is nowhere near the ntfs partition. As said above, the ntfs partition has nowhere to expand, and you'll have to move sda5 and sda6 out of the way first, before expanding sda1.

Ahhh, I see. What is the easiest way to do that?

On the windows on, it had pointers that you could move at the beginning or end of the partition.

Here I can increase the size of the linux partition, but can't create space at the beginning of it so I can move the swap partition into it.

---

### Post by mikewhatever on 2011-03-04
Gparted should have the 'Move' option in the right click menu. 
One thing to be aware of, the UUIDs of the moved partitions will probably change, and if they do, you'll get a 'partition not found' error from Grub. If that happens, you'll need to adjust the UUIDs is /etc/fstab.
A recent backup of personal files is also recommended.

---

### Post by kevb8ll on 2011-03-04
> **mikewhatever said:**
> Gparted should have the 'Move' option in the right click menu. 
One thing to be aware of, the UUIDs of the moved partitions will probably change, and if they do, you'll get a 'partition not found' error from Grub. If that happens, you'll need to adjust the UUIDs is /etc/fstab.
A recent backup of personal files is also recommended.

I assume when I complete the install it will re-write the grub? If so it will know where each partition is?

---

### Post by kevb8ll on 2011-03-04
Hmm, there is now move option. I select the Linux partition and right click, the only options are change, delete and revert.

---

### Post by Quackers on 2011-03-04
From the live cd desktop, can you please run gparted and post a screenshot of it?

---

### Post by kevb8ll on 2011-03-04
Ok I feel a bit of a twit. I realise now I was looking at the installer partitioner and not gparted.

I have run that and have got the following as the opening screen:

[[IMG]http://i6.photobucket.com/albums/y219/kevb8ll/th_Screenshot5.png[/IMG]](http://s6.photobucket.com/albums/y219/kevb8ll/?action=view&current=Screenshot5.png)

I want to move the Linux and swap section along, increaseing swap by 1G and adding the 5G remaining on the end of the NTFS.

I just had a play, I can create a gap at the beginning of the linux partition, but it doesn't seem to want to move into the available none assigned space.

Kev

---

### Post by mikewhatever on 2011-03-04
> **kevb8ll said:**
> I assume when I complete the install it will re-write the grub? If so it will know where each partition is?

Yes, it will rewrite everything, grub, fstab, etc. Since you are reinstalling, just delete sda5 and sda6, adjust the size of sda1, and then proceed installing Ubuntu. Backup any important files from sda6 first.

---

### Post by Quackers on 2011-03-04
No, it won't at the moment, because sda5 and sda6 are logical partitions within the extended partition (sda2).  
What you want to do can't be done from the installer.
In gparted right-click on the swap partition and select "swapoff".
Then right-click again and select "resize/move"
Choose the new size of the partition and ok it.
Click on the green tick in the toolbar to apply the change.

Now you have some work to do.
You need to extend the sda2 partition to the end of the disc (effectively using up the free space). Apply the change.
Then move sda6 to the right (leaving the free space in front of it). Apply the change. It may take some time to complete.
Then move sda5 to the right (leaving the free space in front of it). Apply the change.
When that's done your free space will be at the front of sda2.
Then reduce the size of sda2 so that all the free space is ejected from sda2. Apply the change.
At this point you should have "unallocated space" (not free space) next to the NTFS partition.  Do not increase the size of the NTFS partition with gparted if the operating system is Vista or Windows 7. Which are you using?

Edit Mikewhatever's way is much easier and quicker :-) if you're not bothered about the existing installation.

---

### Post by kevb8ll on 2011-03-04
> **mikewhatever said:**
> Yes, it will rewrite everything, grub, fstab, etc. Since you are reinstalling, just delete sda5 and sda6, adjust the size of sda1, and then proceed installing Ubuntu. Backup any important files from sda6 first.

Good idea. 

So when I've deleted sda5 and 6, I can add my 5G to the NTFS partition and then select the empty partition on install and it will prompt me for swap size and the remainder will be the linux partition?

---

### Post by kevb8ll on 2011-03-04
> **Quackers said:**
> 
At this point you should have "unallocated space" (not free space) next to the NTFS partition.  Do not increase the size of the NTFS partition with gparted if the operating system is Vista or Windows 7. Which are you using?

Edit Mikewhatever's way is much easier and quicker :-) if you're not bothered about the existing installation.

I'm using XP pro, will I be able to extend that OK using Mike's method?

The original linux install is no good, as I no longer have x64 chipset. I now have x32 -so it doesn't matter deleting it.

---

### Post by Quackers on 2011-03-04
You may also be better to delete the extended partition too (sda2).
If you're using Vista or Windows 7 use the disk management screen in Windows to extend the C: partition. It's safer.

---

### Post by kevb8ll on 2011-03-04
> **Quackers said:**
> You may also be better to delete the extended partition too (sda2).
If you're using Vista or Windows 7 use the disk management screen in Windows to extend the C: partition. It's safer.

Hi Quackers, see my previous post. :D

---

### Post by mikewhatever on 2011-03-04
> **Quackers said:**
> You may also be better to delete the extended partition too (sda2).
If you're using Vista or Windows 7 use the disk management screen in Windows to extend the C: partition. It's safer.

+1 Either delete or shrink sda2 from the left, then you should have space to expand sda1.

---

### Post by Quackers on 2011-03-04
I have used gparted before to extend an XP partition and it worked fine. What concerns me is the red circle next to the NTFS partition in gparted. That can mean that a chkdsk may need to be run. Can you boot into XP ok? I would check that before extending it, just to be safe.

---

### Post by kevb8ll on 2011-03-04
> **Quackers said:**
> I have used gparted before to extend an XP partition and it worked fine. What concerns me is the red circle next to the NTFS partition in gparted. That can mean that a chkdsk may need to be run. Can you boot into XP ok? I would check that before extending it, just to be safe.


Will do, I'll report back.

---

### Post by kevb8ll on 2011-03-04
Yep boots up into XP fine.

---

### Post by Quackers on 2011-03-04
That's good. Off you go then :-)

---

### Post by kevb8ll on 2011-03-04
I have a problem. I deleted the linux partition as listed above, I tried to increase the NTFS partition but after 3 minutes it came up with an error. (No detail available). It then reverted back to the previous size.

I haven't installed ubuntu yet, but I can't boot up windows. It comes up with a grub error 22.

Any ideas?

---

### Post by kevb8ll on 2011-03-04
I guess because the partition is deleted, the grub is now deleted. How can I get windows to boot?

Can I sort it from within ubuntu using the live disk?

---

### Post by Quackers on 2011-03-04
Did you apply the change by clicking on the green arrow?
What does gparted show now?

---

### Post by kevb8ll on 2011-03-04
Yes I did. It shows just the NTFS partition and about 18G free space. 

I'm not too bothered about increasing NTFS it would have been nice, but it isn't critical.

I'm more bothered about getting windows to boot before I install 10.10.

---

### Post by Quackers on 2011-03-04
You can still do that now.
In the Ubuntu installer choose manual partitioning.
In the new window double-click on the unallocated space and in the new window create a swap space of your chosen size, but put it at the end of the disc - not the beginning. Change that option. 
Then create a partition for root with a mount point of "/" from the drop down box. The partition type can be logical and formatted to ext4. Then put that at the end of the disc as well (not the beginning). That should leave you free space after the NTFS partition when the installation is done.

---

### Post by kevb8ll on 2011-03-04
Ok brills.

So how can I get Windows to boot at the moment? We need to access stuff on the XP partition and can't boot up at the moment.

---

### Post by Quackers on 2011-03-04
At the moment grub is installed to the mbr of the drive but the partitions it's looking for have now gone, so it panics and refuses to boot anything.
That's what's wrong. You have 2 choices.
Repair the mbr of the disc with the Windows repair cd or (preferrably) install Ubuntu and the new grub will pick up the Windows installation and boot it.

---

### Post by kevb8ll on 2011-03-04
> **Quackers said:**
> At the moment grub is installed to the mbr of the drive but the partitions it's looking for have now gone, so it panics and refuses to boot anything.
That's what's wrong. You have 2 choices.
Repair the mbr of the disc with the Windows repair cd or (preferrably) install Ubuntu and the new grub will pick up the Windows installation and boot it.

That makes sense.

I'll do the latter.

---

### Post by Quackers on 2011-03-04
Probably best.
Take your time and if you're not sure of something just ask.

---

### Post by kevb8ll on 2011-03-04
I have a new error on the install, it's saying that sda is mounted and do I want to unmount. I assume that's yes and it won't overwrite windows partition.

---

### Post by Quackers on 2011-03-04
Did you quit gparted? Maybe shut down and start again from the disc.

---

### Post by kevb8ll on 2011-03-04
> **Quackers said:**
> Did you quit gparted? Maybe shut down and start again from the disc.

Yep that's fixed it.

I'm now looking at your previous instructions to set the space correctly.

---

### Post by kevb8ll on 2011-03-04
> **Quackers said:**
> You can still do that now.
In the Ubuntu installer choose manual partitioning.
In the new window double-click on the unallocated space and in the new window create a swap space of your chosen size, but put it at the end of the disc - not the beginning. Change that option. 
Then create a partition for root with a mount point of "/" from the drop down box. The partition type can be logical and formatted to ext4. Then put that at the end of the disc as well (not the beginning). That should leave you free space after the NTFS partition when the installation is done.

Ok I have done this. I assume to install I select EXT4 from the list like this:

[[IMG]http://i6.photobucket.com/albums/y219/kevb8ll/th_Screenshot1-1.png[/IMG]](http://s6.photobucket.com/albums/y219/kevb8ll/?action=view&current=Screenshot1-1.png)

And then hit install?

---

### Post by Quackers on 2011-03-04
Did you post the right screenshot?

---

### Post by kevb8ll on 2011-03-04
> **Quackers said:**
> Did you post the right screenshot?

Oops, sorry.

[[IMG]http://i6.photobucket.com/albums/y219/kevb8ll/th_Screenshot8.png[/IMG]](http://s6.photobucket.com/albums/y219/kevb8ll/?action=view&current=Screenshot8.png)

---

### Post by Quackers on 2011-03-04
If that partition has been setup with a mount point of / already, just click on install.

---

### Post by kevb8ll on 2011-03-04
> **Quackers said:**
> If that partition has been setup with a mount point of / already, just click on install.

The one highlighted in the screenshot is sda6 type EXT4 with a mount point / (format is also ticked).

---

### Post by Quackers on 2011-03-04
And the free space is in front of it :-)
Shoot!

---

### Post by kevb8ll on 2011-03-04
I'm installing at the moment - but I now have a bit of a panic, because I don't remember selcting dual boot.

I'm definitely putting in the right place - not the windows directory. But I don't remember an option for dual boot.

---

### Post by Quackers on 2011-03-04
That will come about later.
If the installation runs ok you will reboot and Ubuntu should start automatically. Once the desktop loads you can open a terminal and run ```
sudo update-grub
```
Then watch as grub.cfg is run. It should find a Windows Loader. If it does, reboot and you should then get a grub menu asking which OS to boot from. Select Windows the first time, to make sure it works ok.
Then you can reboot again into Ubuntu.

---

### Post by kevb8ll on 2011-03-04
> **Quackers said:**
> That will come about later.
If the installation runs ok you will reboot and Ubuntu should start automatically. Once the desktop loads you can open a terminal and run ```
sudo update-grub
```
Then watch as grub.cfg is run. It should find a Windows Loader. If it does, reboot and you should then get a grub menu asking which OS to boot from. Select Windows the first time, to make sure it works ok.
Then you can reboot again into Ubuntu.

Just re-booted, the grub has picked up the Windows Op but obviously set to Ubuntu as priority.

I'll need to have Windows as the primary boot because the kids use the machine too. Where do I do that?

---

### Post by Quackers on 2011-03-04
Yes, that can be done. It's a little more involved than throwing a switch though.

---

### Post by kevb8ll on 2011-03-04
Ooh I have a bit of a problem, the keyboard isn't being picked up through the USB so I can't manually choose another boot up - only the default.

Any ideas?

---

### Post by Quackers on 2011-03-04
No, I'm afraid not. Maybe reboot again and see if it's the same. Try googling or searching this forum for anything in that respect.

---

### Post by kevb8ll on 2011-03-04
Ok - how do I change the boot order in the grub then Quackers? When I've done that, I'll call it a night.

---

### Post by Quackers on 2011-03-04
Here is a very useful guide for all things grub2 related. Everything you need to know is in there :-)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by mikewhatever on 2011-03-04
> **kevb8ll said:**
> Ok - how do I change the boot order in the grub then Quackers? When I've done that, I'll call it a night.

There is an application called StartupManager in the repositories. It can change the default boot OS.

---

### Post by kevb8ll on 2011-03-04
> **mikewhatever said:**
> There is an application called StartupManager in the repositories. It can change the default boot OS.

That was easy! :D

The keyboard was easy too - I just turned USB support for keyboard on in the CMOS setup.

Mike and Quackers, thank you SO much for your help and patience. I have a working dual boot machine. 

Well I say working, I have some errors with XP, but running checkdisc now and that should fix those.

---

### Post by Quackers on 2011-03-04
Excellent :-)
Bear in mind that with Startup Manager, every time grub is updated, your changes will be overwritten and Ubuntu will become the default system again.

---

### Post by kevb8ll on 2011-03-05
Will do.

XP is working fine now too.

Thanks again mate.

Kev

---

### Post by Quackers on 2011-03-05
You're welcome. Have fun :-)

---

### Post by Quackers on 2011-03-05
> **pasha_kazmi said:**
> can i partition 2 hdds into 1 partition, and if i can, can someone give me a step by step guide please

Partitions are sections of a disc. You can't have a partition that spans more than one disc.
But I'm sure there are other options open to you. Maybe start a thread of your own stating what it is that you want to achieve.

---

