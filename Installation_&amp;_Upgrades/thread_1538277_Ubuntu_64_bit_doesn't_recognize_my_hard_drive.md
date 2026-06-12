---
title: "Ubuntu 64 bit doesn't recognize my hard drive"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by adanedhel728 on 2010-07-24
Well, basically, that's the extent of my problem.  I'm trying to install Ubuntu Lucid on a custom-built machine (specifically, dual-booting with Windows 7), but Ubuntu doesn't seem to be able to find my hard drive to install it.  It can see my external drive, and even my phone's sd card, but it can't see my internal hdd.

I've tried the LiveCD, wherein I got this message before anything else:  
[INDENT]"The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again." [/indent]

And then, while on the desktop, it didn't recognize my hard drive.  

I tried the alternate cd, but I had the same problem (minus the error message), it just doesn't recognize my hard drive.

I tried Karmic, same effect.

I tested the integrity of both the LiveCD and the alternate cd, both checked out.

Right now I'm downloading Xubuntu to see if that makes a difference.  If it does, though I'm not particularly expecting it to, I could install Gnome from there.  I'm also downloading the 32 bit edition just to see if it recognizes my hard drive, but I cannot use the 32 bit edition, so that's just to see if it makes any difference.

Anyway, here's my hard drive and motherboard:

[Seagate Barracuda 7200.12 ST3750528AS 750GB 7200 RPM 32MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive -Bare Drive ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148445")

[GIGABYTE GA-P55A-UD3 LGA 1156 Intel P55 SATA 6Gb/s USB 3.0 ATX Intel Motherboard ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128412")

Don't know if it's relevant, but here's my CPU: [Intel Core i5-750 Lynnfield 2.66GHz 8MB L3 Cache LGA 1156 95W Quad-Core Processor BX80605I5750 ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115215")

Let me know if there's anything else relevant that I can say about it.

Thanks to anyone that can help me out!

---

### Post by adanedhel728 on 2010-07-25
Ok, I'm going to have to bump this because googling has done nothing to help.

---

### Post by marseille on 2010-07-25
> specifically, dual-booting with Windows 7

hi, i'm upgrading my machine and just passing through and saw you...

can you fill in some of the basics just for confirmation?
* how did you format your disk, etc...?

---

### Post by adanedhel728 on 2010-07-25
Well, I just formatted my disk as NTFS since I already have Windows 7 installed, I figured that Ubuntu would be able to see it and repartition it.  Would I have better luck if I repartition it first from inside of Windows?

---

### Post by marseille on 2010-07-25
> Well, I just formatted my disk as NTFS...

Ok then, your brand new hard drive is working fine:D

If I were you, I would defrag the drive and then repartition it with FAT32 since NTFS is only for Windows OS' after XP. Once you do that, you should have a smooth linux installation.

ps... once you reinstall (which I think is the simplest for you) then ubuntu will give you the option of reformating with EXT3 or EXT4. if you are doing a later model of ubuntu I think it's gonna try to do EXT4 but you should read up on that since last I saw it was a bumpy road on that note. fyi- that was a few months ago when i read about it so look it up. either way-- ext is not like FAT so your info won't be insecure like it is on FAT. i just want to make that clear since I'm keeping things as simple as possible for you.

pss: windows has some nice reformating tools but they only give you options for FAT and NTFS. i like GPARTED because it gives me more. i can repartition any drive not only with FAT or NTFS, i can also make partitions for EXT and linux swap drives. if you take the GPARTED route, then you can bypass the extra step of partitioning a drive with FAT. and if you take it another step further and make a linux swap, it's pretty cool.

---

### Post by adanedhel728 on 2010-07-25
Thank you very much.  Now I'll have to do some research to figure out how to use the Windows partitioner, lol.  (It's been awhile since I've used it.)

But, that brings up another issue: Does that mean that I won't be able to mount the NTFS partition after installation?

Edit: But it also *does* see my external, which is also NTFS...  Is that something to be concerned about?

---

### Post by marseille on 2010-07-25
> another issue: Does that mean that I won't be able to mount the NTFS partition after installation?

Edit: But it also does see my external, which is also NTFS... Is that something to be concerned about?

to tell you the truth, i don't have enough info to make a judgment call...

but so far, you've established that you are trying to dual boot Windows 7 and Ubuntu -- which I also do on my netbook. now, we both know that win7 wants to that encryption locker thinga-ma-jig to our main hard drive... what do they call it: bitlocker? i can't remember cuz i yanked that thing off my win7 the minute i saw it (*there are open source alternatives and plenty of forensics tools to replace bitlocker*).

anyway-- is your new hard drive just another addition to your old drive or did you toss the old and make the new one your C: drive and let the encryption thing take over? 

i am suspecting that you didn't let bitlocker take over your external drive because i assume that you had to reformat that extra drive with NTFS. if that's true then Windows probably saw it INITIALLY as a FAT drive -- in which case, it can't really do too much to protect any FAT drive. i don't know too much about bitlocker but is it possible that you needed to tell bitlocker to take that external drive over but forgot? if so, then UBUNTU would have seen your NTFS drive. to see more of what i'm talking about/leading up to, check out how UBUNTU reads and writes to NTFS [https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)

---

### Post by oldfred on 2010-07-25
Check BIOS setttings. Sometimes the default is RAID which then you have to use the text based installer. Other settings may also be an issue. What mode are the SATA ports set to?

You should use the Windows tools to shrink the windows partitions. But do not make additional partitions with the windows tools as you will have to reformat to linux anyway, unless you want a shared data partition. After shrinking make sure windows boots ok it usually want to at least run chkdsk or other updates to recognize its new size. 

If you just want standard install, you then can install to the free space. But if you want separate /home or a NTFS partition to share data with windows you should use gparted in the liveCD to create partitions. Teh installer may not have the ntfs-3g driver as it is set up to install just linux. Once installed you can format as the install include the ntfs-3g driver or use windows to format it. IF you create partitions manually then you have to use manual install and choose the partitions you want.

Resize windows partition info:
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)
Alternate install example win 10.04:
[http://members.iinet.net.au/~herman546/p2.html](http://members.iinet.net.au/~herman546/p2.html)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Full Disk install Lucid Graphical
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by adanedhel728 on 2010-07-25
Bitlocker is actually news to me.  I've never tried to dual-boot Windows 7 and Ubuntu before now.  But I found something online to see how I can get around it ([here]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")) and what it says to do doesn't work for me-- GParted still doesn't see my internal drive.

> anyway-- is your new hard drive just another addition to your old drive or did you toss the old and make the new one your C: drive and let the encryption thing take over? 

There actually isn't an old hard drive, this is the first hard drive to use with this system.  So, I guess the encryption thing has taken over, then?

> Check BIOS setttings. Sometimes the default is RAID which then you have to use the text based installer. Other settings may also be an issue. What mode are the SATA ports set to?

I'm in the BIOS now (typing this on my laptop, of course), and, honestly, I cannot make out whether or not a RAID configuration is turned on.  It's just not very clear.  But, I actually did try the text installer, and it still couldn't see the drive.

> You should use the Windows tools to shrink the windows partitions. But do not make additional partitions with the windows tools as you will have to reformat to linux anyway, unless you want a shared data partition.

Well, Ubuntu still doesn't seem to see the hard drive.

---

### Post by ronparent on 2010-07-25
Try booting the live cd with nodmraid appended to the boot line. If raid meta dat is present bur you don't intend to install to a raid, this should nullify it.

---

### Post by adanedhel728 on 2010-07-25
> Try booting the live cd with nodmraid appended to the boot line. If raid meta dat is present bur you don't intend to install to a raid, this should nullify it.

Thanks, but unfortunately, Ubuntu still couldn't see the hard drive.

---

### Post by Unterseeboot_234 on 2010-07-27
Let me join in this (if you are still keeping this thread alive). 

What I'm finding out is that networking mounts more Win7 partitions than having two hard drives trying to discover one another. What that means is:

1. Win7 must be installed on NTFS.
2. Win7 must create the partitions. The choice of formats are: NTFS or exFAT.
3. When Win7 is running, and with the proper permissions set up, you can see folders on the C:\ drive and the D:\ exFAT 'drive' using a network.
4. Win7 doesn't see a FAT32 created by gparted.
5. Win7 can I/O to an external USB device that is formatted FAT32. So can Ubuntu when it is booted.

So, I would proceed to a RAID setup after I can drop files while in Win7, reboot into Ubuntu and see the same volume. I've learned that Win7 must make the partition. Maybe there is a 3rd-party tool to mount FAT32 in Win7. The Linux ntfs-config tool doesn't see NTFS volumes created in Windows.

In other words, what was possible in XP has now changed because Win7 wants to make the partitions. Microsoft wants coin for exFAT -- which was patented just for flash memory cards.

---

### Post by adanedhel728 on 2010-07-28
Well, I tried [a third-party tool]("http://www.softpedia.com/get/System/Hard-Disk-Utils/FAT32format.shtml") to format the partition as FAT32, and it did successfully format it as FAT32, but still nothing.  It still just doesn't see the hard drive.

To tell you the truth, based on what I understand about how people have in the past managed to get Windows 7 and Ubuntu to dual-boot, I'm not so sure it's an issue with Windows 7.  It seems like Ubuntu just can't see the hard drive.

I'm going to try a Mepis LiveCD just to see if it can see the drive at all.  So far, Ubuntu can't see the drive (and gives me that error), Fedora gave me all kinds of weird errors, Knoppix (though admittedly an old version) drops me to a shell, and Sabayon can't load at all.

Not that I would want to stick with Mepis, of course (I'm really not fond of it).  I just want to see if its a problem with Linux in general or Ubuntu specifically.

---

### Post by oldfred on 2010-07-29
We normally ask to run this when Ubuntu does not work but it may show something unique about your windows. You have to run from a linux liveCD.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by adanedhel728 on 2010-07-29
Ok, I finally figured it out.  I had a *similar *problem as [javyn999]("http://ubuntuforums.org/showthread.php?t=1480746").  (I didn't find that thread until just now, though not for lack of searching.)  I had to move from SATA3 to SATA2, and now it works fine.

Thanks for the help, though, everyone.

---

