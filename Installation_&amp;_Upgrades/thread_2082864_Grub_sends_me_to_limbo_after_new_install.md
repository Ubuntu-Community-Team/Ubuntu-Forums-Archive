---
title: "Grub sends me to limbo after new install"
date: 2012-11-10
forum: Installation &amp; Upgrades
---

### Post by the big e on 2012-11-10
So I have a dual-boot Thinkpad, with Vista and Ubuntu. I decided to re-install everything because Vista was getting messed up.

I installed Vista from disks provided. Okay so far. Have Vista running and also the ThinkVantage utilities that came with the Thinkpad.

Then, I went to "shrink partition"
I shrank the partition to give myself enough space to install Ubuntu in.
Then I gave the newly-created empty space a drive name. Maybe I should not have done that.

Then I took my Ubuntu install disk and ran it. It seems to have worked okay. Version 10-point-something because that's what I had lying around from last time.

Then I was bold and decided to run the updater to take it to 12.04 or whatever the current one is now. While it ran that, I saw various error messages about dependencies.

Then, it told me it was finished installing, and it said I had to reboot. 
Grub came up, and I chose Ubuntu.
Instant error message saying I could not mount "/" and I could press S to skip, M to go into manual mode, or wait.

So what did it do? Install Ubuntu on a partition it now does not see? How far back do I have to re-wind the process in order to get Ubuntu going again? I hope I do not have to re-install Windows to have a clean start. Do I need to re-install Ubuntu or just find some esoteric way of telling where it is?

---

### Post by the big e on 2012-11-10
I should add, Thinkpad uses three partitions, one for Windows and two for its system utilities and recovery software. I can create a fourth to run Ubuntu in, but it does not allow the machine to have more than four. 

Oh, by the way, I think I saw it say it was installing on partitions five and six when it ran the installer.

---

### Post by darkod on 2012-11-10
You might wanna run boot-repair to create the bootinfo and take a look what is where. You can post the link with the bootinfo here so we can take a look too.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Couple of points:
1. When shrinking windows partitions to make space for linux, leave the space created as unallocated and DON'T touch it any more. No creating partitions on it, no drive names, no letters, nothing... Windows can't create linux partitions. Leave the space as unallocated and let the ubuntu installer do the job.

2. The version you mention as 10-piont-something, that "something" makes a big difference. You should really know what you have and be more precise. 10.04 is the previous LTS and can be upgraded directly to 12.04 LTS. 10.10 on the other hand was a normal release and is to old, the repositories are closed so it can't be upgraded (by default).
Now, the errors you received might have been because of that, or maybe it did start the upgrade from 10.04 to 12.04 but didn't finish it.

Lets see what the bootinfo will say. If you do have an unfinished upgrade it might not be easy to fix. In any case, reinstalling windows shouldn't be necessary since they are separate on their own partitions. In the worst case you might need to make a new clean install of ubuntu, and this time I suggest you download the 12.04 ISO and make yourself a cd instead of using what you have at hand from years ago.

---

### Post by the big e on 2012-11-10
thank you, darkod. This sheds some light. But how do I run a bootinfo? Is that something that can be done from within windows? within linux if I could get to it? from a cd-rom? and how do I use it?

also, can I un-allocate the new partition I created from within windows and go back to square one that way?

---

### Post by darkod on 2012-11-11
You can run boot-repair running the ubuntu cd in live mode (Try Ubuntu). The instructions are in the link.

Yes, you should be able to delete that partition(s) and start all over. You should be able to delete it either from windows or using Gparted in live mode. If using Gparted you might need to right-click the swap partition and select Swapoff so that the keys symbol next to it goes away. When it is mounted you can't delete it. Using Swapoff will unmount it.

---

### Post by the big e on 2012-11-12
Thank you. I ended up reinstalling everything clean, since I figured that even if those fixes worked, I wouldn't understand what I had.

---

