---
title: "Resizing Linux Partition"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by Labago on 2011-04-17
When i installed linux to dual boot on my laptop, the installer partitioned 30gb of my harddrive to linux and i now want to add more space to that partition. I have tried to with Gparted but when i right click the partition to add more space, it wont let me select the option to resize my linux partition, any suggestions? Any help would be much appreciated

---

### Post by Dutch70 on 2011-04-17
You have to do it from the live cd or usb stick. You can't work on a disk while you have it mounted.
That's like trying to move a chair while you're still sitting in it. :)

---

### Post by Labago on 2011-04-17
> **Dutch70 said:**
> You have to do it from the live cd or usb stick. You can't work on a disk while you have it mounted.
It's like trying to move a chair while you're still sitting in it. :)

So how would i go about doing that? Im running the 11.04 Natty Narwhal linux distro, should i get that on a usb somehow and run it? then try and add space to this partition?

---

### Post by Dutch70 on 2011-04-17
If you have to download it, use a stable version such as 10.04 or 10.10, or just download the gparted .iso.

---

### Post by Labago on 2011-04-17
Also, one more quick Q. I have about 120gb of free space on my windows partition, but when i try to shrink that from within windows it wont let me. Gparted seems to be able to shrink it but i havent tried, will that harm my windows side of the comp?

---

### Post by Hakunka-Matata on 2011-04-17
what version windows?

---

### Post by Labago on 2011-04-17
> **Hakunka-Matata said:**
> what version windows?

Windows 7

---

### Post by Blasphemist on 2011-04-17
Or you can use the system rescue cd as it includes gparted.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by Hakunka-Matata on 2011-04-17
i think windows 7 has the capability to resize it's partition?  But if you wish to use gparted it should work also.  Do I have to mention backing up?  Do you have the necessary software to reinstall/recover your windows 7 installation if all goes pear shaped?

---

### Post by Labago on 2011-04-17
> **Hakunka-Matata said:**
> i think windows 7 has the capability to resize it's partition?  But if you wish to use gparted it should work also.  Do I have to mention backing up?  Do you have the necessary software to reinstall/recover your windows 7 installation if all goes pear shaped?

Ummm, i dont think i do because i downloaded Windows 7 and put it on a usb i think, prob lost that by now haha. But i do have most of my things backed up that need to be backed up, dont really want to deal with losing windows tho...any safe way to do this?

---

### Post by Hakunka-Matata on 2011-04-17
> **Blasphemist said:**
> Or you can use the system rescue cd as it includes gparted.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

--> Blasphemist:  is the rescue disk a windows disc?  can you tell the OP how to resize his windows Partition?

---

### Post by Dutch70 on 2011-04-17
If you resize windows7 from anything other than windows, you're just begging for problems. There are several steps to go through to shrink windows, just search the web for how to do it.

Edit:
I can't remember everything, but you need to defrag probably a couple times. Delete & turn off restore points. Things like this are probably at the end of your disk you're trying to shrink and it will more than likely mess windows up if you don't go through the right process.

---

### Post by Labago on 2011-04-17
> **Dutch70 said:**
> If you resize windows7 from anything other than windows, you're just begging for problems. There are several steps to go through to shrink windows, just search the web for how to do it.

Edit:
I can't remember everything, but you need to defrag probably a couple times. Delete & turn off restore points. Things like this are probably at the end of your disk you're trying to shrink and it will more than likely mess windows up if you don't go through the right process.

Ok thanks a lot for the advice, ill search around for how to do that. So then once i have that shrunk, is adding that space to my linux partition easy as pie?

---

### Post by Dutch70 on 2011-04-17
> **Labago said:**
> Ok thanks a lot for the advice, ill search around for how to do that. So then once i have that shrunk, is adding that space to my linux partition easy as pie?

Compared to windows? ...Yes!!!

How easy depends on your system.

Btw, any time you mess with partitions, there is a chance of data loss or worse. Even if by user error.

---

### Post by Labago on 2011-04-17
hahaha alright sounds good, almost everything is easier on linux, hence why windows is getting replaced

---

### Post by Dutch70 on 2011-04-17
After you shrink your partition, you may want to run check disk once or twice to make sure you're not getting any errors.
Good luck, Let us know how it goes.

---

### Post by Blasphemist on 2011-04-17
I hope all is going well. My experience with this has lead me to put it off. I tried to use Win 7 disc management to shrink it's partition. It would have shrunk by 1828 MB. Big woop! I defraged about 5 times and it isn't like the old days where you could see the files by color being defragged. At some point it told me that IE history files couldn't be moved, I believe when I tried to shrink it. It never told me of anything else that couldn't be moved. I deleted the IE history, and I don't even use IE and very seldom even boot windows. I defragged multiple times and each time it still took a long time. If it was accomplishing anything, I couldn't point to proof.

I have seen people in these forums recommend using GParted to shrink the Windows partition. I could imagine issues but don't know that there are. In the end, I no longer depend on Windows for anything. I keep it just for the ability to check how to do something in Windows that comes up trying to help someone else with issues. My Kaspersky subscription runs out in a couple months. I am pretty sure that at that time, windows is getting kicked out. I'll completely reconfigure and install multiple builds of Linux. Ubuntu, openSuse, Arch, Mint, Fedora, etc. I'll have Gnome, KDE, Unity, Xfce and likely versions of some of them. I'll have to depend on experience, critical thinking and memory for helping windows users.

---

### Post by Dutch70 on 2011-04-17
Blasphemist if you're having/had that much trouble shrinking your hdd, you may want to open "Disk Utility" and check the SMART Data on your hard drive to make sure there are no bad sectors.

---

### Post by Blasphemist on 2011-04-17
Thanks Dutch, I'm looking at the smart data. There is a ton of information here and I'd never looked at it. I don't see any errors and the assessment of each item is either good or n/a. I'm running a self test now though.

---

### Post by Labago on 2011-04-17
Ok all is well, i found a tutorial thing on how to shrink the windows partition and did so, only by 20 gigs though thats all i could get, i may try to get more later but i then booted linux on a usb and added that 20 gigs to the linux partition with gparted and i had no errors! woo thanks a lot for the help everyone

---

### Post by Dutch70 on 2011-04-17
Nice! 

So, all is good then & this thread is [Solved]? 

Blasphemist, If you have bad sectors, it will show in red & be very obvious. Let's hope you don't have any.

---

### Post by Labago on 2011-04-17
ya this thread is solved, idk how to actually mark it as such tho, im a newbie here

---

### Post by Dutch70 on 2011-04-17
See my sig ;)

---

