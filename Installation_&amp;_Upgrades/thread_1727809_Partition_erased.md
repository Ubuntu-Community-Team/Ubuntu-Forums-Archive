---
title: "Partition erased"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by chapacha on 2011-04-13
Hello,

I have had Ubuntu and Windows 7 in dual boot before with no problems at all. I recently got a new machine I was planning on using for gaming. I had Windows 7 Ultimate 64-bit installed on it and used it for awhile then installed Ubuntu on a smaller partition. I was getting some trouble with certain programs so I figured after a bit of research that Ubuntu hadn't installed right. I then wiped the Ubuntu partition. When I started up the computer again it brought up the Windows Boot Manager screen and I could choose Windows or Ubuntu. The Ubuntu choice did nothing and just required me to restart. Well I logged in on Windows and it still read that partition as Ubuntu's. So I wiped it again and formated it as NTFS and restarted my computer. It was back to just a regular partition. I then proceeded to try to reinstall Ubuntu. I did the steps and told it to install along side another OS. The installation was done but a fatal error occurred. It said that it couldn't load the boot manager and gave me 3 options. To either choose another partition to install on, continue without and find one online later or cancel the installation. None of these worked. I clicked on all of them and then 'OK' and tried and tried and waited and waited to have them go forward from that menu. I was stuck of a day. Finally I got impatient and just turned off the computer. I got back into the installation menu and behold, it gave me the option to install it on all of the hard drive. There were no partitions left. Really scared that something happened I quickly exited the Ubuntu install and tried to just boot up windows. Nothing. Not a thing is there. I put in the Windows disc to try to repair the start up thinking maybe the Ubuntu install wiped out the boot manager so it just couldn't boot. Yet again, there was absolutely nothing for it to repair. Not a single thing left. Now my hard drive is nothing but wiped clean and I have no idea why or how. :confused:

What I need help with is if there is a way to somehow 'find' the Windows partition again or at least recover some files. If anyone knows anything about why or how this error happened please let me know. I just need all the help I can get because this is really annoying having to reinstall everything again. I did have all my photos of my family backed up thankfully. I need your guys help and I know you can deliver at least some helpful information. If this is some sort of boot manager error, then please let me know how I can fix this without, preferably, wiping the hard drive.

Thanks.
Nikolas

---

### Post by earthpigg on 2011-04-13
go easy on the wiping of partitions, next time, and the turning off of a computer in the middle of the operating system installation. 

but, at this point, moving forward:

easy approach: put an ubuntu livecd in, and hit 'try without making changes'. once ubuntu loads, open the file manager and see if you can see the hard drive from there.

if not, see if system -> administration -> gparted recognizes the partitions.

intense approach: [photorec]("http://www.cgsecurity.org/wiki/PhotoRec"). very reading, labor, and time intensive, but it does a good job. this is the tool the FBI uses to gather evidence on people that have "emptied the recycle bin" of evidence on their Windows computers.

---

### Post by chapacha on 2011-04-13
Thank you very much!
 
Yeah I know how risky it is to do what I did, but it was just sitting and really not even thinking for a whole day. I'll try that tool out as well!
 
Nikolas

---

### Post by Mark Phelps on 2011-04-13
If your drive was really "wiped clean", as you stated, NOTHING you do will get the files back. Period.

But I suspect that really, it was only erased. That does not actually wipe the drive clean.  It doesn't even remove the files.  Same with formatting.  The files and data are all still there -- just not easily accessed.

Personally, I've had abysmal results using Linux utilities to recover Windows partitions/files -- but you may have better luck.

The more you mess with the drive, however, the bleaker the chances of getting anything back.  So, the first thing you need to do is remove the drive from use and set it up to be connected as an external drive to a working PC.

If you have access to a Windows PC, you can try downloading and installing GetDataBack for NTFS from Runtime Software.  Their free version will scan the drive and tell you what it found. But, it's likely to take all night to do an in-depth scan.  You have to purchase it to recover the actual data.

---

### Post by Gr72 on 2011-04-13
Can someone help me with this problem??

I am a newbie when it comes to linux. About a year ago I installed Ubuntu into a dual boot with winows 7. I accidentally deleted the Ubuntu partition from within windows and left it. After a registry error in the windows partition I re-installed windows over everything and has been working fine. But, now I am getting back into linux and have been trying to install Ubuntu ans use a Backtrack liveCD but I can't and recieve this error:

Buffer I/O error on device sr0, ;ogical block 993427
Buffer I/O error on device sr0, ;ogical block 993428
Buffer I/O error on device sr0, ;ogical block 993427
Buffer I/O error on device sr0, ;ogical block 993428

SQUASHFS error: squashFs_read_data failed to read block 0x7583e78f
SQUASHFS error: unable to read id index table

BusyBox v 1.10.2 (Ubuntu 1:1.10.2-1 Ubuntu7) built in shell (Ash)
Enter 'Help' for list of built in commands




If Any one can help me with this, that would be great, I have been picking my brains over this and have googled it but have come up with nothing. Thanks

---

