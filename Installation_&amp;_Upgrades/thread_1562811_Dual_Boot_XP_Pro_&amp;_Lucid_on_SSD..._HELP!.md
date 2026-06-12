---
title: "Dual Boot XP Pro &amp; Lucid on SSD... HELP!"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by DonkeyShark on 2010-08-28
I just bought a Kingston 128GB SSD for my laptop.  I've moved my 160GB HDD to the 2nd drive bay for a storage drive on the NTFS system.  I'm splitting the 128 between XP Pro and Lucid Lynx.  Previously, I had Lucid and XP splitting my 160 HDD.  Lucid was screaming fast on the HDD, but I formatted the drive and put fresh installs on my SSD.  Now, XP is screaming fast on the SSD, but Lucid takes a long time to boot up.  It also hangs often during routine tasks.  I pretty much gave up on Ubuntu because of this as I just don't have teh time it takes to try to solve the issues.  I'd really like to use my Linux installation.  I've read so many different ideas as to how to "properly" install Linux on a SSD, however I don't know my head from my **** in the Linux world and can't seem to follow anyone's instructions even though I have a degree in Mathematics and an IQ of 147.  I feel like a retarded kid. Every instruction I follow either doesn't apply at one step or another or it yields an error.

I've read that you first need to properly align the drive ???  I have no idea what this means or why it would even matter.  Can anyone explain this or invalidate these claims?

I've also read that you need to round off the drive?  No clue what that means...

I've also read that SSDs require TRIM support but that Lucid doesn't provide it.  Again, I have no idea what TRIM support is.  Can anyone explain or invalidate this claim?

I've also read that NCQ must be enabled... Again, don't know what that is or how I would attempt to enable it.

I've also read that you need to update to GRUB2 or your install won't work.  Again, I'm confused... I thought GRUB was just the screen you get to after BIOS that allows you to choose your operating system.  I assume I'm incorrect and lend that there must be much more to what GRUB or GRUB2 is.  

Wouldn't the newest Lucid build just have all the necessary components/support for SSDs built into it by now?  I don't get why there are so many hoops to jump through to make Linux work.  Shouldn't it just work?  I'm pulling my hair out... please advise.

Thank you kindly in advance

---

### Post by Herman on 2010-08-28
> I've read that you first need to properly align the drive ???  I have no  idea what this means or why it would even matter.  Can anyone explain  this or invalidate these claims?Yes, any kind of flash memory will work a little better and probably last longer if you can have the start of your partition aligned on an erase block boundary.
That is because flash memory needs to be erased and re-written a 'block' at a time.
The size of the erase blocks varies between manufacturers, so you need to get your information at your SSD manufacturer's user forum. Yours will be complicated by the fact that you didn't install Ubuntu at the start of the disk. That will mean you're going to need all of your mathematical skills to determine the starting sector for your Ubuntu partition for optimal file system alignment, after you find out the erase block size from your SSD manufacturer, if they will give out that information.
> I've also read that you need to round off the drive?  No clue what that means...:confused: I don't know either.
> I've also read that SSDs require TRIM support but that Lucid doesn't  provide it.  Again, I have no idea what TRIM support is.  Can anyone  explain or invalidate this claim?
 TRIM empties the erase blocks that are not being used by the file system, saving time when you need to write to them later on because they will already be empty. I installed the latest version of hdparm to enable TRIM support and installed a program called DiskTRIM in my SSD Ubuntu installation. 
Before I could get that working I needed to update my SSDs controller firmware with a BIOS flash, but that was a year ago already and if your SSD is new you probably won't need to flash you firmware, I'm not sure.
> I've also read that NCQ must be enabled... Again, don't know what that is or how I would attempt to enable it.
I don't know what NCQ is or I've forgotten.
> I've also read that you need to update to GRUB2 or your install won't  work.  Again, I'm confused... I thought GRUB was just the screen you get  to after BIOS that allows you to choose your operating system.  I  assume I'm incorrect and lend that there must be much more to what GRUB  or GRUB2 is.  If you're using Lucid Lynx you're already using GRUB2, not that it should matter. 
> Wouldn't the newest Lucid build just have all the necessary  components/support for SSDs built into it by now?  I don't get why there  are so many hoops to jump through to make Linux work.  Shouldn't it  just work?  I'm pulling my hair out... please advise.Because SSD drive controller and flash memory technology is subject to a lot of scientific and engineering research and improvements and competing manufacturers want to hold their cards close to their chests, there's no possible way for any operating system to be able to offer blanket support for all SSD drives.
Your SSD manufacturer's web forum will be the best place to look for the correct advice about partition alignment and TRIM support for the particular make and model of SSD you have.
Ubuntu Lucid Lynx should just work in just about any kind of drive including any flash memory or SSD.
Currently, (or at least the last time I checked), Linux and in particular, Ubuntu with its timely adoption of the ext4 file system was considered to be far more advanced than Windows in terms of adaptability to SSD use. Ubuntu was the first Linux OS to adopt the ext4 file system as its default file system since Karmic Koala 9.10, and in 10.04 Lucid Lynx we also have a 1mb empty space before the starting sector if Ubuntu is installed first in the disk. That should mean Ubuntu will install and work well in most flash memory and SSDs without too much user intervention.

Your Ubuntu should work well and be very fast in an SDD. I had Lucid Lynx booting in about 3 seconds when I had mine tuned for fast booting, and with standard settings it still boots very quickly, I haven't bothered timing it lately. I love using Ubuntu in my SSD drive, it's as fast as lightning whenever I click on anything, and jobs that normally take a while to complete are generally much faster than with a HDD.

---

### Post by Herman on 2010-08-28
This old thread contains a lot of useful links about installing Ubuntu in an SSD and tuning for optimal perfomance, [COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[ext4 without journaling]("http://ubuntuforums.org/showthread.php?t=1404664").
I'm sorry it's a hard thread to follow, but I was just posting things as I was finding out information and I never did get around to re-writing all that in a nice tidy sequence that would be easy for others to follow. The links are probably as important if not more important than the thread itself.  :D

---

