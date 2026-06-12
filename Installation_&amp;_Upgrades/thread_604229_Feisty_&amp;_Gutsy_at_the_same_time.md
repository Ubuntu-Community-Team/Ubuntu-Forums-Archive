---
title: "Feisty &amp; Gutsy at the same time?"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by maura_ea on 2007-11-05
This may be the stupidest question, but I have to ask it.

I had terrible problems with my wireless 43XX broadcom chipset when first upgrading to Gutsy upon its release. I had to resort back to Feisty - which is still a great system but is lacking the desirable NTFS writing - in order to use my wireless.

Since Gutsy's release, a lot of suggestions have come about to fix the 43XX chipset and I'd like to give Gutsy another try. However, it took me ages to upgrade and then resort back because I have a dual boot system and everything needs to be done in a specific way. I would prefer not to wipe my systems, install Windows, install Gutsy and then realize I can't fix Gutsy afterall.

So my question is this: Is it possible to install Gutsy on my current system that has Feisty & Windows and still retain the original two operating systems in case Gutsy still does not work?

---

### Post by dcstar on 2007-11-06
> **maura_ea said:**
> This may be the stupidest question, but I have to ask it.

I had terrible problems with my wireless 43XX broadcom chipset when first upgrading to Gutsy upon its release. I had to resort back to Feisty - which is still a great system but is lacking the desirable NTFS writing - in order to use my wireless.

Since Gutsy's release, a lot of suggestions have come about to fix the 43XX chipset and I'd like to give Gutsy another try. However, it took me ages to upgrade and then resort back because I have a dual boot system and everything needs to be done in a specific way. I would prefer not to wipe my systems, install Windows, install Gutsy and then realize I can't fix Gutsy afterall.

So my question is this: Is it possible to install Gutsy on my current system that has Feisty & Windows and still retain the original two operating systems in case Gutsy still does not work?

Resize you existing partitions to make hard drive space, and install into the free space.

You will be able to boot whatever you have.

---

### Post by Doggles on 2007-11-06
Yep - it's possible, and no, it's not a stupid question.

What you're after is a triple boot system, which is happily pretty easy to do under Linux. It shouldn't be that difficult to achieve for your system provided that you do it carefully. You can use a live CD to re-size and arrange your hard disk partitions (needs to be done with a live CD as the disk needs to be not mounted while it's being repartitoned).

Here is the workflow to use, and some caveats to watch out for - have a good google and a look through this forum for triple booting tips before you do anything, and if you need any help on a specific point, then repost here.

1. Resize your partitions to create a bit of space on your disk using gparted from any ubuntu live CD

2. Use Gparted to create a new partition for your third operating system - so that now your partitions will look like this: 1. Windows, 2. Feisty, 3. Swap 4. New partiton for Gutsy - note that your two linux installations will be able to share the same swap, so you only need one of those. WARNING - leave all your existing partitions as they are, just resize to get free space, then create a new ext3 partition for Gutsy. ALSO - there is a limit to how many primary partitions you can have (I think it's 4 actually, so the above setup should be OK), after that, you're into using extended partitions - do-able, but more complicated... Provided that your setup is quite simple like the example above, you should be OK. Write down your partition numbers from GParted so that you know what's where

3. Install Gutsy to your newly created partition using the manual install option - WARNING - you need to familiarise yourself with how your partitions are numbered to make sure you're writing to the right one!!! - ALSO - you need to ensure that while installing Gutsy, you install GRUB only to Gutsy's root - NOT to the MBR (this then ensures that on boot-up, your system continues to use Feisty's copy of Grub - ie: the one that you already have set up correctly, so that you will still be able to get into windows, and if you want to get rid of Gutsy again later (or even try another distro for that matter, all you'll have to do is write over Gutsy and nothing will be broken)

4. Edit Feisty's grub menu to include an option to chainload to Gutsy's copy of grub, and hence get into Gutsy. You can get into editing the menu in Feisty by opening a terminal and doing: gksudo gedit /boot/grub/menu.lst   and then add in the correct entries for your new install - there's loads of help on this forum for doing that (note that Grub's numbering system for partitions is a little different, but if you've successfully set up a dual-boot already, then you probably know all about this?

5. Reboot and you should have an option to get into Gutsy. If it's not to your liking, you can easily use Gparted again from a live CD to delete Gutsy and resize your old partitons back to use the full disk, or you can retain this partition for testing out any distro that you like - just remember to install grub only to root and not to the MBR for anything new that you add.

I do this all the time to play around with new distros - I currently have two main drives, and use a separate partiton for /home, so that whatever I do to my main distro I don't lose all of my data, and I'm running Ubuntu Studio (Gutsy), Xubuntu (lightweight distro for running Quake 4, and other games under Wine), SimplyMepis and Debian Etch. I finally completely got rid of XP a couple of months ago. If you've got plenty of drive space, it's fun to muck about with different distros just to see what works best for you - many of them are very similar to each other though! - I find that I spend 80%+ of my time in Ubuntu Studio.

Best of luck with all of this, again, if you need any help, repost here and I'll do my best (but bear in mind that I'm still a bit of a n00b at this myself!):)

---

