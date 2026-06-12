---
title: "Help w/Partitioning during Installation"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by amageed on 2006-06-18
Hi all,

I'm having trouble getting Ubuntu Desktop 6.06  installed, specifically during the partitioning. I have Windows XP (on C:\) and I'm trying to partition D:\ for Ubuntu so I can dual boot. I have some stuff on D:\ so I don't want to totally format or use the whole drive just for Ubuntu.

So, I go to "Manually edit partition table" and resized D:\ to make some space for Ubuntu and I noticed it defaulted to "ext3" as the partition type. I then added another partition from that and made it "linux-swap." Is this correct?

Then I get to the "mount" screen where I need to select the root "/" and swap. I see the drive options as hda1 and hda2 or such, and hda2 is what matches my D:\ drive... so I selected "/" on the 1st dropdown for hda2, and "swap" on the 2nd dropdown for hda2 also. Once I proceed, it tells me it had errors creating the SWAP on the specified drive and to go back. :confused: 

I've been messing with it for awhile now and I can't figure it out.

Can someone please give me some step by step instructions on how to do this properly?

One other question: what's the recommended/minumum PC speed (MHz) required to install Ubuntu? I found the min. reqs. for memory and HD space but not speed.

Thanks,
A potential new Linux user :)

---

### Post by ????? on 2006-06-18
mount "linux-swap" as "swap". NOT the same partition you put ubuntu on.

Also, it wont be shown as a drive letter on windows unless you download one of those ext2 drivers

---

### Post by amageed on 2006-06-18
Hmm that's what I thought would happen once I setup the "linux-swap" but at the mount screen all I saw was hda1 and hda2, not the "linux-swap" that I just made. Neither did I see the one that showed up as "ext3."

---

### Post by catlett on 2006-06-18
I dislike the partitioner with the install. I do my partitioning ahead of time with gparted live. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) It is a small download, only 30 mb. It is a live cd that has just gparted on it. Gparted is a partitioner program like Partition Magic.

Quickly to your install. Your lucky it came back with an error, you almost wiped out your entire Windows install and all your data on D.

hda1 and hda2 in windows would be C and D. If you had made those other 2 partitions they would have been hda3 and hda4. Somehow the partitions weren't formed correctly and didn't show up.

Get out of the install disc. Boot to gparted. Select resize/move a partition. Choose D (or in gparted hda2) The partitioner will show your partition in a bar graph. You can drag the right side of the graph to shrink your partition. Let's say for the sake of arguement you are going to give Ubuntu 10gb. And of that 10 you are giving 1gb to swap and 9gb to the system.

Slide the graph over until it shows 10gb of free space after your partition hda2. Pick "resize". 
Now there will be "unallocated" space. Right click on that and choose "new". You'll get the bar graph again. Drag right to left until the partition is 1gb. Sel ect under "filesystem"  "linux-swap". Let it default to whatever it wants in the "create as". Hit "add"
Right click on the "unallocated space" again. Don't move the graph. Select under "filesystem"  "ext3" let it default what it wants in "create as". Hit "add".
Make sure to hit "apply" at the top.
It will run the partitioning.

Now reboot into the install cd. Choose "manually edit the partition table". DON"T TOUCH hda1 and hda2. They will be automatically mounted.
In front of your 1gb partition which should say hda3 choose "linux-swap" (or just swap, I forget), In front of your 9gb which should be hda4 choose /  ( / is the label for root)
Last is to check off the circles next to your swap and / that have the heading "format?". DO NOT check off these circles after hda1 and hda2.
Let the installer run. When you boot, you will have a 1gb swap and a 9gb root partition with Ubuntu on it. C and D will be icons on your desktop. 
Good Luck.

---

### Post by amageed on 2006-06-18
Thanks, I'll give that a shot :)

---

