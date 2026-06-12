---
title: "Live CD boot corrupted windows partitions"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by li-nux or lie-nucks? on 2010-10-11
Has anyone else seen this?
Have a PC with 2 internal SATA HD's one with Windows 7 installed on and the other with the Windows user folders on. Also have a USB stick plugged into the back for Windows Ready Boost. So thought I would install Meerkat to an external WD 250GB USB hard disk. 
Tried booting live CD from two different discs 10.10 RC and 10.10 final to give it a go before commiting to install and found that one of the internal HD's was thrashing away. So rebooted to see what was going on.
It was at this point that for some reason a message popped up about no OS being found. When I did try and recover Windows it ran chkdsk and made what I can only describe as a mirror of the OS drive onto the second HD where all the user folders were stored. On the second attempt it did the mirror thing again but in reverse so I ended up with a second version of the user folders but no OS.
Luckily I have everything backed up and was able to restore everything as the Windows recovery and GParted tools could do nothing with the disks.
Any ideas why this should happen as I had not even begun the installation or partitioning process and is there any way that I can _SAFELY_ install 10.10 without blowing everything away again?

---

### Post by Mark Phelps on 2010-10-12
Having to guess, I would say that GRUB was installed (by default) to your first internal hard drive.  That is HOW the installation works -- unless you know enough to go to the Advanced tab and change GRUB to install to a Linux filesystem partition -- and most folks don't even see that option.

This is a common failure of USB installs in that folks are not made aware that the default install WILL modify their internal hard drive.  They just presume (and quite rightly!) that the USB install will NOT touch their internal hard drives in any way.

---

### Post by li-nux or lie-nucks? on 2010-10-12
Thanks Mark but had not even begun installation which is why I am confused. I was aware of the grub advanced install option and assume that I would choose /dev/sdb (as that is what my USB disk is recognised as) to install the bootloader to? Would love to be able to run 10.10 from the USB disk but don't even want to boot from the CD for fear of reprisal from the family (again) for destroting their lovely Windows OS!

---

### Post by li-nux or lie-nucks? on 2010-10-14
Update: Have tried booting Live CD once again from a new disc burned today. Same thing happened but this time managed to get Windows to boot. Looking at windows disk management tool and have found that the second hard disk has been converted to RAW format.
Why would just booting the live CD cause this? Haven't even taken steps to install yet and to be honest pretty much put off Ubuntu now because of this even though I have been a dedicated Ubuntu user for several years.

---

### Post by li-nux or lie-nucks? on 2010-10-15
Anyone??????
I surely cannot be the only person who has experienced this issue?

---

### Post by Mark Phelps on 2010-10-15
You mean, have you been the only person to trash a preinstalled Win7 machine messing around with Ubuntu?  Not from the other posts I have seen.

But if that second partition is really RAW, you have totally hosed that machine!

My suggestion, if you don't want the family to lynch you once they discover what you have done, is to go to a Windows 7 forum (sevenforums.com is one of the best), and post a request there asking if there is some way to restore that second partition you hosed.

I'm hoping that the lesson you learned from this is -- don't mess around with a PC until AFTER you have made sufficient backups to be able to recover from any damage you might cause.

---

### Post by li-nux or lie-nucks? on 2010-10-15
Thanks Mark but this wasn't messing around as I said all I was doing is booting live from the CD. I have be using Linux since 1995 and work with Linux servers all day long so do know my way around. Just that I have never come across this issue before and wanted to see if anyone else had. From what I see it looks like booting live from this version seems to read or do something with the existing partition table and being a Windows 7 NTFS partition it doesn't like it. Looking at the posts on the install & upgrade threads there seems to be a lot related to partition issues with Windows 7.
I am able to restore fairly quickly as you may have missed in my previous posts that I have full backups and images of everything something I learned from work as a Data Centre Admin.

---

### Post by oldfred on 2010-10-15
Testdisk may repair a RAW disk without losing data but no guarantees.

[http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_a_lost_and_damaged_NTFS](http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_a_lost_and_damaged_NTFS)

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by li-nux or lie-nucks? on 2010-10-16
Thanks oldfred. Will probably run testdisk next time round but use windows based imaging software just restore everything back to what it was. Have found now that Ubuntu seems to be not the only distro that causes me this problem. Have tried out Fedora and Mandriva both of which produced the same problem. Thought that maybe there was a duplicate disk signature but even when changing the disk signature and trying again the problem still happens.

---

### Post by linuxonbute on 2011-06-16
> **li-nux or lie-nucks? said:**
> Has anyone else seen this?
Have a PC with 2 internal SATA HD's one with Windows 7 installed on and the other with the Windows user folders on. Also have a USB stick plugged into the back for Windows Ready Boost. So thought I would install Meerkat to an external WD 250GB USB hard disk. 
Tried booting live CD from two different discs 10.10 RC and 10.10 final to give it a go before commiting to install and found that one of the internal HD's was thrashing away. So rebooted to see what was going on.
It was at this point that for some reason a message popped up about no OS being found. When I did try and recover Windows it ran chkdsk and made what I can only describe as a mirror of the OS drive onto the second HD where all the user folders were stored. On the second attempt it did the mirror thing again but in reverse so I ended up with a second version of the user folders but no OS.
Luckily I have everything backed up and was able to restore everything as the Windows recovery and GParted tools could do nothing with the disks.
Any ideas why this should happen as I had not even begun the installation or partitioning process and is there any way that I can _SAFELY_ install 10.10 without blowing everything away again?
Did you get this sorted? I just booted my wife's win7 (64bit) tosh laptop with live ubuntu 11.04 and just checked that hardware was seen. Re-booted but win 7 corrupted and it did a repair which fixed it. Tried the same again but this time just booted live 11.04 and then shut it down Win 7 corrupted again.
It seems to me this is a serious bug. Downloading 64bit ubuntu to see if this will work ok.

---

### Post by li-nux or lie-nucks? on 2011-06-16
Sorry never did get to the bottom of this. The only thing I did discover after digging around a bit more was that the Windows partition was being converted to RAW format.
Got fed up with having to restore each time and not brave enough to try again.:(

---

