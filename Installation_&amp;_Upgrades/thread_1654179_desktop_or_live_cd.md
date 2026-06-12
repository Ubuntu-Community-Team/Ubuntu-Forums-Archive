---
title: "desktop or live cd?"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by thomast77 on 2010-12-28
I have an old dell desktop running XP. I want to setup a dual boot with Ubuntu. I have already created a 15mb primary ntfs partition on my harddrive which I plan to install Ubuntu to. I was looking through the documentation on the Ubuntu website for Dual boot instructions as I have never setup dual boot before. The documentation I read recommended I use the live cd of Ubuntu to install it. What is the difference between installing the Desktop Ubuntu versus the Ubuntu livecd if any? Which should I use? or does it matter?

---

### Post by Rubi1200 on 2010-12-28
Hi and welcome to the forums :)

First things first, Ubuntu does not use NTFS, so formatting the partition does not really make much sense. The default file-system for Ubuntu is Ext4:
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

Did you mean 15GB? Because 15MB is not going to do anything!

For dual-boot information, see here:
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

The LiveCD is simply the way you can try Ubuntu without making changes to your computer.

By default, it will install the regular desktop version.

More information:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
(this page also has instructions how to make a LiveCD)

Importantly, before you start: please post the specifications because if it is an older machine you may not be able to run the regular Ubuntu install. In that case, we can advise you regarding other, lighter options.

---

### Post by thomast77 on 2010-12-28
Ubuntu will work on fat32 right? I would like to be able to move files back and forth between xp and ubuntu if need be. I figured I could make that choice during the install process? But if not then I will use disk management to reformat it to fat32. I did mean 15gb. The system is a Dell Dimension L733r 733mhz intel processor 512mb ram. Thank You for your time :)

---

### Post by Rubi1200 on 2010-12-28
Please take a screenshot of your current setup from Disk Management so we can get a better idea of what you have.

If you want to share data between Ubuntu and Windows you can set up an extra partition to do so.

Trying to force Ubuntu to install to FAT32 would be like trying to force Windows to install to a Linux file-system; pointless and potentially damaging to your hard-drive.

If you post the screenshot, we can advise you as to the optimal setup for your situation.

---

### Post by Sef on 2010-12-28
Both FAT32 and NTFS are both designed by Windows for Windows OSes; Ubuntu can read and write to them. For installing Ubuntu just use the default file system, ext4.

---

### Post by thomast77 on 2010-12-28
ok here is a screenshot of disk management. I also have screenshots of device manager if you need that? Also I have a second hard drive installed that can be used to share files. WinXP is on C: of course. I would like to install Ubuntu on D: or the second partition of disk0.

[IMG]http://img.photobucket.com/albums/v380/billm7/thomast77/diskmgmt.jpg[/IMG]

---

### Post by Rubi1200 on 2010-12-28
This looks fine to me. Your current D drive has enough space for Ubuntu to install.

Here is what I suggest.

Download the 10.04 version (I know 10.10 is the latest, but 10.04 is an LTS release, meaning it is supported for 3 years with updates):
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

Burn the image to CD:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Boot the computer and choose to try not install first.

Then, go to Applications > Accessories > Terminal and post the output of the following command:
```
sudo parted -l
```

I would also ask that you go to System > Administration > GParted and post a screenshot.

I am being cautious because I want to make sure this ends well (which it will).

Once you are at this stage, post back here and we will move to the next stage.

Thanks.

---

### Post by thomast77 on 2010-12-28
It gets as far as the Ububtu Load screen. It loads for a good minute or 2. Then the CD drive spins down and nothing happens. I never even get to the screen where you make your choice to install or try it out.

---

### Post by Rubi1200 on 2010-12-29
How much RAM is available and what graphics card do you have installed?

Thanks.

---

### Post by thomast77 on 2010-12-29
512mb ram and an ATI Radeon 7500

---

### Post by Rubi1200 on 2010-12-29
RAM should be just about good enough.

Graphics are often an issue.

Try this procedure to boot the LiveCD:

Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter:

nomodeset

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --**

Now hit Enter and hopefully you will be at the desktop.

NOTE: you may need to try F6 and Esc first.

If the nomodeset option does not work, try it with xforcevesa.

Let me know how it goes please.

---

### Post by thomast77 on 2010-12-29
neither works. The last line in nomodeset if it helps is:
init: ureadahead-other main process (1013) terminated with status 4

xforcevesa makes the monitor go completely black

---

### Post by Rubi1200 on 2010-12-29
Would you feel comfortable installing with a text-based installer?

We have seen this type of situation before and, sometimes, using the Alternate CD works better.

---

### Post by thomast77 on 2010-12-29
I am not familiar with any linux commands but if there is a guide or something I can probably figure it out.

---

### Post by Sef on 2010-12-29
> Rubi1200
Would you feel comfortable installing with a text-based installer?

> thomast77	
I am not familiar with any linux commands but if there is a guide or something I can probably figure it out.

The text-based installer is very easy.  The only difficult part that you may face would be manually partitioning.  Though, if I remember correctly, an option exists for installing Ubuntu in the largest free space.

---

### Post by Rubi1200 on 2010-12-29
I agree with Sef on this one.

All the instructions are fairly easy to follow up until the partitioning time.

What I suggest is the following:

try the Alternate CD (it is on the same page I linked to before, just further down). You burn the image to CD as with a regular image.

Start the computer and go through the process.

When you get to the partitioning stage, stop, and post here and we can try and walk you through it.

(although I, personally, will be going from memory on this one; last text-based install I did was a few months ago).

---

### Post by thomast77 on 2010-12-29
Ok I will give it a try. I will post sometime tomorrow as I am checking out for the night. By the way Thanks for all the help :)

---

### Post by Rubi1200 on 2010-12-29
No problem, you are more than welcome :-)

I will keep an eye on this thread and help as much as I can when you post again.

---

### Post by thomast77 on 2010-12-29
ok I am at the partition screen.

---

### Post by Rubi1200 on 2010-12-30
Sorry for the delayed response.

What do you see?

Based on your previous posts, there should be a partition for Windows (C drive formatted to NTFS) and the D drive which you want to use, which was also NTFS.

They will probably be identified as sda1 and sda2.

Try and post what the partitioner tells you is there.

---

### Post by thomast77 on 2010-12-30
Thats ok I'm in no real hurry. I am just playing with this really so I can learn more about Ubuntu and linux. I see several options to resize then an option to manually partition, I took a look at manual and it shows all the partitions. They are all listed as ntfs. I assume I need to select manual then select the second partition on disk0 or do I need to use one of the other options? I don't think really need to resize it. Also I looked at some documentation and it seems I will need a swap partition? So maybe I do need to resize and leave about 2000mb for the swap partition? Or does it automatically do that for me?

---

### Post by Rubi1200 on 2010-12-30
The good news is that the Alternate CD works for you.

I always go with manual partitioning. It may seem a bit more scary, but I feel it gives you a more fine-grained control over what is happening.

I cannot remember if the Alternate CD automatically creates a swap partition; I don't think it does so, yes, you would have to do that.

When you say "all the partitions," what do you mean? 

Here is a guide that might help with partitioning:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Sorry, read your post again:
> I assume I need to select manual then select the second partition on disk0Yes, if the size is right (it was about 18GB as I recall from the screenshot) and then you can format it. Use ext4 and / for the root partition. I would leave about 2GB free for swap (depends on your RAM). I don't know if you want a separate /home partition, but you might just be able to squeeze it in.

Also since you only have 2 primary partitions, I would leave it as is and not create an extended partition first (which many people have to do since you can only have 4 primary).

I assume disk 1 (marked as Backup) is either an external or a secondary drive?

Here is how it would look:

16GB /
2GB swap

or

5GB /
2GB swap
11GB /home

This is just a suggestion of course. You are free to partition according to your needs.

Whatever you do, if you are unsure, you can always go back or ask here.

I hope this helps.

---

### Post by thomast77 on 2010-12-30
Ok I was able to get it installed. I created a 2mb swap and the rest was for the OS. formatted ext4. Then after install is complete it reboots to start the system the first time. The grub Dual boot comes up. Ubuntu is selected. It then proceeds to cut the monitor off or throw some colored snow on the screen. I don't think this is going to work with my video card. Is there anyway to install a driver for the card or something? Or is it just not going to work on this computer? Thanks again for all your help :)

---

### Post by thomast77 on 2010-12-30
the first time I got colored snow on the screen. Every time after that. Grub comes up I select Ubuntu a little cursor blinks in the upper left hand corner the screen flashes a few times then the monitor clicks off as if it lost the signal from the computer.

---

### Post by Rubi1200 on 2010-12-31
Hi,
what graphics card do you have installed? I need the specifics please.

What you describe is definitely a graphics issue; depending on the card, we may be able to find a workaround.

Is Windows booting normally?

---

### Post by thomast77 on 2010-12-31
ATI Radeon 7500
and windows is working fine.

---

### Post by Rubi1200 on 2010-12-31
Okay, let's try this:

when the computer boots and the GRUB menu comes up, when you see the entry for Ubuntu highlighted press "e" to edit.

Find the line that ends with > quiet splash

Remove quiet splash and type nomodeset then "Ctrl" + "x" to boot.

If this gets you to the desktop we can make it more permanent.

Let me know please.

Other options to try instead of nomodeset include xforecevesa, noapci, nolapic although I would try each one separately to see what works.

Hopefully, these links will also help:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by thomast77 on 2010-12-31
No luck using nomodeset I see a bunch of lines across the screen loading everything. Then it stops the screen flashes a few times and then just a black screen. The hard drive light shows no activity. The other modes all loaded the same except they cause the monitor to click off like it is losing signal. Like in windows when the power save feature shuts off your monitor after a certain time. I will look at the link and see if it will help. Let me know if you have anymore ideas. Thanks for the help :)



Edited to add:   Looks like the link you provided would only work if I can get to the desktop. Is there away to add this driver to the install CD? If so I would need a guide with instructions to do that. Or maybe someone else has already done it?


Edited again to add:  Unless it can be done at the command prompt if I can get there.

---

### Post by Rubi1200 on 2010-12-31
Did you try any of the other boot parameters I mentioned at the end of my previous post?

Meantime, I will keep looking for a solution.

EDIT:
try using this parameter instead of what I suggested before:
pci=use_crs

In other words, same procedure and add this after quiet splash (no need to remove quiet splash this time).

Let me know if it works

Another option:
radeon.modeset=0

---

### Post by thomast77 on 2010-12-31
I did try all the other parameters in your previous post. pci=use_crs cut the monitor off. However I got a bit further just a bit using radeon.modeset=0 it brought me to a screen I haven't seen yet and it appears to be in another font its acting like it took just for a second before it quit again. Here are the last few lines:
fsck from util-linux-ng 2.17.2
ubuntu: clean, 136148/1099440 files, 591407/4394496 blocks
*starting apparmor profiles

then it just stops. No hard drive activity. Nothing.

---

### Post by Rubi1200 on 2010-12-31
Hmm, this is interesting.

Those lines of text you saw are quite normal. That is the kernel "chatting," telling you it is doing this and that etc.

Try  radeon.modeset=1 instead and see what happens.

I have to go now, but will definitely be back to try and help you figure this out.

---

### Post by thomast77 on 2010-12-31
that one doesn't work either? Cuts the monitor off.

---

### Post by Rubi1200 on 2011-01-01
Any chance you can switch the monitor and try another one?

That may help narrow things down as to whether this is a problem with the monitor, the video card, or something else.

Another thing to try (seems obvious I know) is to power down then unplug and replug relevant cables in for the monitor, motherboard, drives etc. Maybe there is a loose or defective cable?

---

### Post by thomast77 on 2011-01-01
But windows still works and I just tried knoppix 6.2 and it boots straight to the desktop no problem. I think it is Ubuntu it doesn't have the drivers. And there is no way of getting the drivers installed unless I can get to the desktop. As much as I wanted to try Ubuntu. I think I am going to have to try another distro. Thanks for all your help though we gave it a good go And I really appreciate it.
Thank You 
Thomas

---

### Post by thomast77 on 2011-01-01
Could you recommend any other versions of linux I might be able to try?

---

### Post by Rubi1200 on 2011-01-02
Hi,
you don't mention which version of Ubuntu you ended up installing. If it was 10.04 (as I recommended), then it may well be an incompatibility issue.

There are some options; either try again, but with 10.10 (the latest version) or have a look at some of the following distributions:
Puppy Linux
Linux Mint Debian Edition
PCLOS
Zorin
Mandriva
MEPIS
Peppermint

More information can be found here:
[http://distrowatch.com/](http://distrowatch.com/)

Read the information on each one, and others, decide what you like the look of and try a LiveCD version first. If everything works, go for an install.

Good luck!

---

### Post by thomast77 on 2011-01-02
it was 10.04 alternate I installed. I will give 10.10 a try. Thank You again for all your help I appreciate it.

---

