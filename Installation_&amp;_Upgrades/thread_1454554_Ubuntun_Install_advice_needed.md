---
title: "Ubuntun Install advice needed"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by Nwwmac on 2010-04-14
I've been using Ubuntu 9.1 virtualized on an Intel iMac (7,1) for a while. I am thinking about running without visualization but I'm not sure what would be the best way to do it. 

My OS X install is 10.6.3 and I have Windows 7 installed under Apple's Boot Camp. 

Ideas: 

#1. Can I load Windows 7 and install Ubuntu from there, ie. on the partition created by Boot camp? When I boot the Boot Camp partition I can choose between Windows 7 and Ubuntu? For some reason I think this sounds too easy...

#2. I have an external drive that is in HFS format that contains a clone of my OS X install. It has lots of space and is boot-able (the clone is boot-able). Can I create a new partition there and install Ubuntu on it? If so, do I use Disk Utility, rEFit or just the Ubuntu installer (it uses Grub, right?)

Any advice would be very welcome. I'm hoping to learn more about Linux by having a 'real' installation to muck about with. :)

---

### Post by gunnarlinux on 2010-04-14
> **Nwwmac said:**
> I've been using Ubuntu 9.1 virtualized on an Intel iMac (7,1) for a while. I am thinking about running without visualization but I'm not sure what would be the best way to do it. 

My OS X install is 10.6.3 and I have Windows 7 installed under Apple's Boot Camp. 

Ideas: 

#1. Can I load Windows 7 and install Ubuntu from there, ie. on the partition created by Boot camp? When I boot the Boot Camp partition I can choose between Windows 7 and Ubuntu? For some reason I think this sounds too easy...

#2. I have an external drive that is in HFS format that contains a clone of my OS X install. It has lots of space and is boot-able (the clone is boot-able). Can I create a new partition there and install Ubuntu on it? If so, do I use Disk Utility, rEFit or just the Ubuntu installer (it uses Grub, right?)

Any advice would be very welcome. I'm hoping to learn more about Linux by having a 'real' installation to muck about with. :)

To pretty much answer your question, yes, use Boot Camp. It's Apple, its supposed to sound easy. Patronizing your external drive should work, just use the Ubuntu installer first, then boot camp. What kind of mac are you using? On an iMac or a G5 it would be a lot simpler than on a macbook.

---

### Post by Nwwmac on 2010-04-16
I'm 0 for 2 so far. :confused:

1. It seems the Boot Camp Assistant won't make more than one Windows partition. I run Windows 7 via Boot camp just fine, and Boot Camp Assistant simply offers to remove it when run. 

2. I tried to use the Ubuntu 9.10 install disk I made but that got tricky when it came to partitioning. I had made a 200 GB partition on an external drive and wanted to install Ubuntu there. The 'wizard' interface did not show that location - it wanted to divide the Windows 7 partition on the main disk.

Using the 'Advanced' button showed the external disk but it asked me things I was unsure about. I made a 50GB swap file, which took forever to create, and then tried to finish the install. 

I guessed at the mount point - choose / - and got an iMac that would not boot, just a black screen that said GRUB with a blinking cursor. The reason I chose / was that I wanted to be prompted for what partition to boot from when booting the external drive. I guess I learned the hard way that / affects more than the external drive. 

*******

I've restored the OS X partition and am back where I started. I'm going to have to think about this some more.

---

### Post by earthpigg on 2010-04-16
50gb swap is huge. shoot for 4, or less. this is the same as a "windows page file", if you are familiar with that term... using a part of the hard drive as backup RAM so your computer doesn't lock up if you run out.

you want an ext4 partition to have the mountpoint of / --- this is probably what you were thinking of when you made the 50gb partition. / is going to be your primary ubuntu partition. 


> Using the 'Advanced' button showed the external disk but it asked me things I was unsure about. I made a 50GB swap file, which took forever to create, and then tried to finish the install.


on the right track. create a 50gb ext4 partition with the mount point of /. create a 4gb partition as "swap" -- or split the 50gb into 46gb for /, and 4gb for swap.

towards the end, you will see a final confirmation screen with an 'advanced' button. click it, and make sure the bootloader also goes on the external hard drive -- then you can tell your mac to boot from USB when you want to use ubuntu (you can tell a mac to do that, right?), and simply don't have the external hard drive plugged in when you turn on the computer if you don't want to use ubuntu.

---

### Post by Nwwmac on 2010-04-17
Thanks for your suggestions. I'll keep them handy for sure. 

I think my first order of business will to find a way to backup my Windows partition. Time Machine and my Mac cloner won't do Windows and as a result it took some time to re-create it (getting OS X back was a snap). 

I took the opportunity of making the Windows partition larger - because the Ubuntu install wizard wanted to place it there. Ubuntu can use NTFS partitions, right? What would I gain by going with EXT?

---

### Post by earthpigg on 2010-04-17
> **Nwwmac said:**
> 
Ubuntu can use NTFS partitions, right? What would I gain by going with EXT?

it can read and write to them, but i wouldn't install ubuntu onto an ntfs partition unless wubi is the route you are going.

as a root filesystem for a linux system, there hasn't been nearly the amount of testing and refinement with ntfs that ext3 or ext4 has.

consider this logic, from the point of view of a linux developer: "Why would i test and develop linux tools to maintain and repair NTFS? anyone using it is obviously going to be relying on windows, anyways."

now, consider the same logic from the point of view of a windows developer: "Why would we at Microsoft spend our resources making sure windows tools can fix/repair/maintain partitions with NTFS filesystems hosting Linux? Our customers should be using Windows, not Linux."

ntfs isn't the "tried and true" option here, ext4 is.

furthermore -- if you do have difficulties with ntfs on your / partition, and then post here asking for advice... very few (if any) posters here will have had any experience with it, and thus the vast majority will be completely unable to help you. Windows tech support venues will be similarly clueless.


edit: if you want Windows to be able to read your linux filesystem, however, consider using ext3 combined with [this]("http://sourceforge.net/projects/ext2fsd/"). there are no omg-huge-must-have advantages of ext4 over ext3 that i am aware of.

---

### Post by Nwwmac on 2010-04-25
I've taken another run at getting Ubuntu running on my iMac. This time I ran Wubi from within Windows 7. Wubi gave an odd error message that I could not get rid of: pyrun.exe cannot find disk. After waiting a bit Wubi did launch and download Ubuntu 9.10. The installer completed normally as far as I could tell. 

Here's where it got a bit odd. Rebooting gave me a choice between Windows 7 and Ubuntu, just as it should. When I chose Ubuntu all I got was a text screen:

GNU Grub 1.97~beta4

Minimal BASH-like editing is supoorted.... ect, etc... 

sh:grub>

So my question is, has something gone wrong? Or do I just need to find out what command grub needs to launch Ubuntu? 

If I can get this to work I will have the set up just as I want. OS X by default, and the other two systems juts a reboot away. So close...

---

### Post by Nwwmac on 2010-04-25
I tried a few guesses at the grub prompt and got one interesting result. 

"boot ubuntu" yielded "no kernel loaded"

I also tried Wubi's troubleshooting suggstions, chkdsk /r, file.000, etc. and found nothing (yes, show hidden files iss turned on).

---

### Post by Nwwmac on 2010-04-26
It seems this is a know - and lingering - bug with Wubi installs. Nice. 

[http://ubuntuforums.org/showthread.php?t=1337149&highlight=wubi+%2B+windows+7](http://ubuntuforums.org/showthread.php?t=1337149&highlight=wubi+%2B+windows+7)

---

### Post by Nwwmac on 2010-04-28
I gave up on Wubi as it seems to be a dead end. 

I succeeded in getting the 10.04 beta running using rEFIt. 

Now I'm chasing down a sound issue that seems to be plaguing a lot of other Mac/Ubuntu users. 

One step at a time... 

:-k

---

