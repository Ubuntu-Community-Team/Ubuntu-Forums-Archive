---
title: "Dual Boot on Vista and RAID 0 Array Problems?"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by kipling100 on 2008-01-07
Hi,

I'm considering dual booting Ubuntu 7.10 on my existing Vista system, but I had a question regarding RAID 0 arrays.  Currently, I have a RAID 0 array set up using an Intel RAID controller on my ASUS P5B-Deluxe.  

As I understand it, I have to shrink the current Vista partition and then install Ubuntu on the unused space.  Do I have to do anything special to make sure the Ubuntu installer recognizes the RAID 0 array?

Thanks in advance,

Dennis

---

### Post by kevpatts on 2008-01-10
Dennis,

I don't think you'll be able to do this. Linux doesn't recognise hardware RAID at installation. "RAID" in the linux world is nearly always software RAID. If you attempt this I suggest you will just see two distinct drives, each with free space.

The way I got around it was to install a seperate drive for Ubuntu, set it as the primary boot drive in my BIOS and install. I then switch between OS's by changing the primary boot volume in the BIOS.

Have a read of a post I've just put up and it might be worth tracking it. I don't think there's gonna be a solution soon though! [http://ubuntuforums.org/showthread.php?p=4110038#post4110038](http://ubuntuforums.org/showthread.php?p=4110038#post4110038)

Kevpatts

---

### Post by kevpatts on 2008-01-11
I tell a lie: [http://ubuntuforums.org/showthread.php?t=630644](http://ubuntuforums.org/showthread.php?t=630644)

---

### Post by JonnyBlazexx on 2008-03-19
I also have the same problem.  I have my vista install on a raid 0 array (2x74g raptors).  I read somewhere that if i plugged in only the harddrive to install Ubuntu, that it would be better.  I installed ubuntu on my 3rd harddrive, while the other raptors were unplugged.  I then shut off my computer, plugged back in the raid array, installed easy bcd and tried both options for the ubuntu installation (grub located on mbr and not on mbr).  Neither seems to work at finding my ubuntu installation on the other hard drive.  I'm sure that if I tell my computer to boot from the 3rd harddrive, that i can get into ubuntu that way, but I really want a simple choice like bcd gives my laptop.

---

