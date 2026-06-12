---
title: "Tri-boot: Windows 7, Windows XP, and Ubuntu"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by Tom_ZeCat on 2010-06-03
I didn’t think I would ever need a tri-boot machine, but I do.  I need a PC that gives me the choice of booting to Ubuntu 8.04, Windows 7 64-bit, or Windows XP 32-bit.  My machine is already a dual boot with Windows 7 Ultimate and Ubuntu Hardy Heron.  These two operating systems are on separate physical hard drives.  Ubuntu is on the original 250 gig master drive and Win 7 is on the 1 TB slave drive.  I installed each OS completely independently of the other with the other hard drive not plugged in.  Originally, I set the PC up as an Ubuntu only PC on that one 250 gig drive.  Later, when I needed Windows, I unplugged the 250 gig drive and installed Windows on the 1 TB one.  Then I plugged the original drive back in and, in Ubuntu, edited the menu.lst file under /boot/grub, per the instructions in this post so that Grub would give me the menu choice of either Windows 7 or Ubuntu: 
**[Dual Boot Two Hard Drives]("http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot")**

It works great.  It was a wonderful way to install two OSes cleanly and independently of one another.  

You must be wondering why on earth I would desire to add yet another operating system to the mix.  It’s because of Quicken for Palm OS, the application that was once the answer to my prayers, but has lately been my nightmare.  I used to never know how much money I had in the bank because I always lost track, never entering my receipts into Quicken.  Then I got a Palm and put Quicken for Palm on it and always entered everything as soon as I bought it.  I came home and synced with Quicken for Windows and thus always kept absolute track of my money.  

Then Palm went out of fashion and so no sync drivers were written for any 64-bit OS.  Yet for my photography work I need a PC with 4 gig of memory, which requires a 64-bit OS.  I researched the issue and learned it can be done via Bluetooth into Windows 7, but I’ve had no luck getting it to work.  I added Virtual PC to Win 7 and tried with Windows XP/64-bit, but also had no luck.  Win XP/32 would not install under Virtual PC in Win 7.  There’s probably a way to get this to work, but I’m spending a ton of time trying to solve it.  Meanwhile my transactions are piling up on my Palm without getting synced into Quicken for Windows.  I know for a fact that all this runs perfectly under Windows XP/32-bit.  

I therefore plan to partition 200 gig of my 1 TB drive into a logical drive onto which I’ll install Windows XP/32-bit.  Onto it will go all my Palm scheduling software and Quicken.  When the computer boots up, I need to have the choice of Windows 7, Windows XP, or Ubuntu Hardy Heron.  I’m hoping to keep the same basic setup I have now with the 250 gig Ubuntu hard drive as the master and the other one as the slave.  I imagine I’ll need to edit the menu.lst file again.  Here’s how it was edited previously, per the instructions in the **[Dual Boot Two Hard Drives]("http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot")** post: 

> title              Windows 7
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1


Do I just leave it like that?  Then when I choose Windows and it goes over to the slave drive, will it give me the choice of Win 7 or Win XP?  If anyone has advice on my turning this into a tri-boot, I would be grateful for it.  

There is one other option, but thinking of it makes my head spin.  I had heard there is Palm scheduling software for Linux that is capable of syncing with Palm devices.  I could install that and then install WINE and Quicken for Windows under Linux.  Thinking of that makes my head spin.  It doesn’t seem like as good an option when I know for certain all my Palm stuff and Quicken run great under Windows XP/32.

---

### Post by jbakuwel on 2010-06-03
Hi,

You might want to try the WXP compatibility mode VM that is available for download from the Microsoft website? Available for free for W7 Pro, Ult.

Alternatively, install WXP on your 2nd harddrive. Assuming your 2nd harddrive will have two partitions: one for W7 and one for WXP, your grub config for these two would look like:

title Windows 7
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

title Windows XP
root (hd1,1)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Good luck!
Jan

---

### Post by Tom_ZeCat on 2010-06-03
Thanks, Jan.  Already tried the Windows XP compatibility mode.  I got all the software to run, except that I could not get it to wire sync, and I couldn't get the Bluetooth connection working.  So gonna do the dual boot.  

Thanks for the info on Grub.  Gonna do that.  Now I'm off to find info on partitioning Win 7.  They've discontinued Partition Magic.  Looks like MS built that kind of functionality into Win 7.  Otherwise there's Partition Commander.

---

### Post by darkod on 2010-06-03
You said you plan to install XP on logical drive. Not sure if you are just using MS terminology here, but to point out that drive and partition is not the same, although MS calls partitions drives.
Having said that, if your idea was XP on logical partition, you won't be able to boot it directly from grub. If you install it on logical partition, XP boot files will get combined with win7 boot files on the win7 primary partition.
After that grub has no choice but to call the windows bootloader, which will then give you options for 7 and XP. So it will be two stage process.

If you want to keep it shorter, and use only grub, as I would prefer, you will have to:
- create the XP partition as primary, not logical
- before installing XP, boot ubuntu and use Gparted to move the boot flag from win7 partition onto the XP partition
- only then install XP. windows depends on the boot flag and when it finds it on the same partition it will keep XP boot files on its partition too. That is the only way I am aware of to boot two windows versions directly from grub

---

### Post by _Mark_ on 2010-06-03
Why not if you are just going to use xp for quicken and syncing with  a palm is to install it virtually with VirtualBox (or you're prefered program) in either Win7 or hardy

I would personally go down that route and there is a lot of good information and guides in the virtulisation forum

Edit

Stoopid me ](*,) I have just read you post again and you say you have tried Virtual PC unsuccessfully in Win7, I would still try with VirtualBox in hardy.

I had no problems installing xp in VBox in lucid and my iphone synced ok with itunes

---

### Post by Tom_ZeCat on 2010-06-03
Frustrating.  I've got problems.  I set up the menu.lst file in Grub the way you said, jbakuwel, but it's not working.  The menu comes up and offers Windows 7, Windows XP, and Ubuntu.  If I choose Windows XP, I get this: 
> Error 12: Invalid device requested

If I choose Windows 7, Windows XP attempt to come up and takes forever on the splash screen, but never loads.  I can then restart and boot to Windows XP in safe mode, but I can't come back in regular XP.  

If I choose Ubunutu, Ubuntu comes up just fine.  I reverted to the old menu.lst file, the one that worked with the dual Win 7/Ubuntu boot.  If I choose Win 7, XP struggles to boot up, but doesn't make it; then I can start up and get booted up in safe mode only.  As before choosing Ubuntu works fine.  

In Ubuntu I can access both logical drives on the 1 TB drive and can see where both Win 7 and Win XP are installed.  

What's wrong and how do I fix it?

---

### Post by darkod on 2010-06-03
> **Tom_ZeCat said:**
> 
In Ubuntu I can access both logical drives on the 1 TB drive and can see where both Win 7 and Win XP are installed.  

What's wrong and how do I fix it?

Did you install both windows on logical partitions? Did you see my previous post that you can't boot windows from logical partition?

And please don't use 'drives', it's misleading term. A drive is a physical disk, HDD - Hard Disk [COLOR=Red]Drive[/COLOR]. Logical drive doesn't exist, that's partitions we are talking about.

Run the boot info script as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

and post the content of the results file as explained. It will show details about your boot process.

---

### Post by Tom_ZeCat on 2010-06-05
Microsoft documentation has referred to partitions as "logical drives;" (drive D, E, F or whatever) so, yes, I was using Microsoft terminology.  In any event, the goal is to get XP onto one partition and 7 on another on the same physical drive while keeping Ubuntu on the other physical drive and then be able to choose between the 3 OSes at bootup.

All right, I royally screwed this one up and am starting over.  Therefore I've killed the extra partition on the 1 TB drive and then did an Acronis (True Image) restore of my PC as it was when I had only XP on it.  I also reset menu.lst to the way it was in my original post.  Now the computer is working fine as a dual boot between XP and Ubuntu.  

That way I can do the Palm syncing and financial work I desperately need to in Quicken.  I have another Acronis image of the PC as it was with Windows 7 and all my apps installed.  If need be, I can restore to 7.  Any important data files of mine I've been saving to twin external hard drives (a copy onto each one), so there's no danger of data loss unless somehow both of them died.  

I'm not going to make the mistake of going into this without enough info this time.  I've found a tutorial on how to dual boot Windows 7 and XP here:  

[http://www.sevenforums.com/tutorials/8057-dual-boot-installation-windows-7-xp.html]("http://www.sevenforums.com/tutorials/8057-dual-boot-installation-windows-7-xp.html")

It has instructions on how to set up a dual boot either by starting with XP on the system first or with 7 on it first.  For me it would be best to start with 7 since that installation has things set up with lots of my apps tweaked exactly how I want them.  What I'm thinking is to approach it like this:  

1. Acronis restore my installation of Win 7
2. Disconnect the 250 gig drive that has Ubuntu
3. Follow the instructions in the link I quoted above to set up a dual boot with XP and 7 on the same hard drive, installed to different partitions
4. Reconnect the 250 gig Ubuntu drive, leaving menu.lst as is.  

If I do it this way, Grub will give me the choice of Windows or Ubuntu; then if I choose Windows, Bootloader will give me the choice of XP or 7, right?  I could live with that.  It might be slightly more convenient to have Grub give me a 3-way choice, but this setup sounds simpler.  With the Ubuntu hard drive disconnected, I can concentrate on a dual boot with 2 versions of Windows only with no interference from Grub or Ubuntu and only reconnect Ubuntu when I'm ready.  Good strategy?  

I guess another option would be to make the 1 TB drive the primary and the 250 gig the slave, then to use Bootloader to choose between Win XP, 7, and Ubuntu.  I don't know if I'm comfortable with that.  My policy in the past has always been to have any of my Microsoft products keep their hands off anything that has anything to do with Linux.

---

### Post by ottosykora on 2010-06-06
I have similar installation which does work. I have 
primary w7
primary XP
primary w98se
log u10.04
log debian
log fedora

grub legacy driving that from separate grub partition. 
Grub does nice hide and unhide the primary partitions and boots the choosen one.
BUT!
w7 lost some parts of its nice functionality by that.
Example: full system backup , the w7 own imaging function does not work any more, so does not the restore from earlier made image.
The reason is, that w7 will search whole disk and when it finds some system partition which is hidden (xp and w98 in this case have to be hidden primary) it will simply refuse work, providing error logs saying that the operation was aborted since some hidden partition is present on this machine.

The only way around it seems to be the use of w7 own bootmanager according to some infos from some windows forums.

---

### Post by darkod on 2010-06-06
If unplugging the ubuntu disk makes you feel safer, no problem. Just make sure you are booting from that disk when you plug it back in, or you won't see grub.

If you want the three way boot, and you currently already have XP installed right? Just create the ntfs partition for win7 from ubuntu with Gparted, and use Gparted to turn off the boot flag on the XP partition, turn it on on the win7 partition.

After that boot with win7 dvd and install on the partition you prepared. That way the boot files will remain separate.

If the win7 install was new, no need to restore the acronis image really.

But it should work either way.

---

### Post by Tom_ZeCat on 2010-06-06
@ottosykora
You might give the link I posted about Win 7/XP dual boots.  I think they talk about a workaround the problem of Win 7 recoveries not working under dual boot, or do a search of sevenforums.com.  As for the system image capabilities, you could use a third-party utility like Acronis or Norton Ghost.  

@darkod
I may want to Acronis restore Windows 7 because I spent hours and hours setting that install up, installing and tweaking apps, etc.  Fortunately, the instructions in the link show how to do it starting with either XP or 7.

---

