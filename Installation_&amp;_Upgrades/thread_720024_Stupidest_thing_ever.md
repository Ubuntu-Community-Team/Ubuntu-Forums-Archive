---
title: "Stupidest thing ever"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by Badmons on 2008-03-09
I ordered a dell Powerdge 440 server about a week ago installed windows and it showed 2 gigs only out of what should be 2 X 160 drives. I then uninstalled it and forgot about it for awhile. I just yesterday ran the Build and Update Utility Bootable CD Version 3.5  disk that comes with the server (in other words the installation disk). It was ready to insert the OS disc but it didn't have xp so i picked windows server 2003 like an idiot and then it made partitions and all that crap and put the linux bootable graphic install thing on the harddrive(like the one for ubuntu) and when it asked for the Windows Server 2003 disc I put the XP disc in. It then ejected it saying it was the "my fault". And now today i got a live cd of Ubuntu and tried to run it but it doesnt run the CD it goes to hard drive and tries to run the Dell Installation thing that it put on the harddrive yesterday. Yes i have my boot order with the CD first. It's like it doesn't recognize the disk even though my other computer's did. So i tried to run it in GRUB which the Dell Install thing put in and i can't get it to boot from a CD does anyone know how to make GRUB boot from a CD or what's wrong with the CD/computer that makes it not autoboot from the CD?

---

### Post by tgalati4 on 2008-03-09
If you can't switch the boot order in the BIOS, then it's possible that the Master Boot Record contains a bootloader that ignores any disk that is not a Windows Server 2003 disk.

You can try swapping the drives.  The second drive shouldn't have a boot loader on it yet so you can start fresh.

Your second biggest mistake is using Windows.

---

### Post by Badmons on 2008-03-09
I know it was stupid to use windows I was planning on getting Ubuntu in the first place but when I was getting a wireless USB at Best Buy I saw windows XP. Ill try that then edit this if i find out if it works.

---

### Post by Badmons on 2008-03-09
DIDNT WORK I tried switching the hard drives first then I tried unplugging the first one and then after unplugging the first one I turned the computer on with the Ubuntu CD in it and it says no boot device. Sounds like it can't read the stuff in the disk or what? Do i have to have something like GUMP to run it?

---

### Post by tgalati4 on 2008-03-10
The Ubuntu CD that you used, is it a commercially-printed CD?  If not, then you should run the "Check CD" option on another machine to make sure it's intact.

---

