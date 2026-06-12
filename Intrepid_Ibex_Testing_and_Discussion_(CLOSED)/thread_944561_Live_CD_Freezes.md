---
title: "Live CD Freezes"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by winhamwr on 2008-10-11
Problem: Installer and "try ubuntu" options in live CD both freeze right before the 3rd section on the loading bar

I'm trying to give intrepid ibex a go as a fresh install on my current system that I dual boot win xp and hardy heron on. What I've done:
1. I downloaded the amd64 8.10 beta iso (filename is ubuntu-8.10-beta-desktop-amd64.iso from [http://releases.ubuntu.com/releases/8.10/ubuntu-8.10-beta-desktop-amd64.iso](http://releases.ubuntu.com/releases/8.10/ubuntu-8.10-beta-desktop-amd64.iso)) 
2. I burned the iso to a disk using hardy
3. I rebooted with the disk in the drive, which brings me to the ubuntu screen
4. I selected the first option (try ubuntu without making changes)
5. The bars bounced back and forth for a while and then it began filling up (the loading bar), but it freezes right before the 3rd segment
6. I then tried the install ubuntu option and it freezes in the same place
7. Concerned that it might have been a bad DL or burn, I repeated 1-6 with the exact same results

8.04 runs just fine on this exact system and I'm not sure what I should be doing to try and debug this problem. Can anyone give me any advice about other things I might try in order to narrow it down?

specs:
Intel core 2 quad Q6600
4 gigs RAM
ASUS EAH3850/G/HTDI/512M Radeon HD 3850 Card - Retail
ASUS P5N-T Deluxe LGA 775 NVIDIA nForce 780i SLI ATX Intel Motherboard

---

### Post by Kevbert on 2008-10-11
Have you performed an md5sum on the ISO.  You can do this via terminal
```
md5sum *filename*
```  Have you burnt the CD at the slowest possible speed to minimize errors ?  Have you checked the CD via the bootmenu option ?

---

### Post by winhamwr on 2008-10-12
Thanks Kevbert. The md5sum showed that the download was correct, so I did two more burns at the lowest speed and the second one was succesful enough that I'm replying to this from my succesful intrepid beta install (woot for the new kernal the supports my wifi dongle with no hassle).

---

### Post by weaselonfire on 2008-10-13
i am having the exact same problem.  This is on my everex stepnote laptop.  I had vista home premium and I wanted to kill it and got for ubuntu 8.04.  The dvd i made checks out fine according to the boot loader but when i say try ubuntu it freezes at almost the 3rd bar.  I have tried this with two hard drives.  I had the same problem when trying Xubuntu on this same machine.  Any help?

---

### Post by winhamwr on 2008-10-13
My "Try Ubuntu" didn't work either, but the install worked succesfully, for what it's worth.

---

### Post by weaselonfire on 2008-10-13
I was having a very similar problem with my everex stepnote laptop.  I did a little searching and came up with this page 
[http://www.poplarware.com/everexlinux.html#install](http://www.poplarware.com/everexlinux.html#install)

from what i can see the problems are the realtec 8139c ethernet driver and the sdhci card reader driver. I am now downloading the alternate release of 8.04.  If what i have read is correct it should install fine if i tell it to skip over those two drivers.  Then i can go back and try to get them working later.  

Hope that helps a bit i will post back if this works.

---

### Post by Kevbert on 2008-10-13
> **weaselonfire said:**
> I was having a very similar problem with my everex stepnote laptop.  I did a little searching and came up with this page 
[http://www.poplarware.com/everexlinux.html#install](http://www.poplarware.com/everexlinux.html#install)

from what i can see the problems are the realtec 8139c ethernet driver and the sdhci card reader driver. I am now downloading the alternate release of 8.04.  If what i have read is correct it should install fine if i tell it to skip over those two drivers.  Then i can go back and try to get them working later.  

Hope that helps a bit i will post back if this works.

Have you tried the F6 with blacklist command with the standard CD ?  The main difference between standard and alternate install CD is one is graphics based and the other is text based (alternate is normally used for PCs with low ram memory).

---

### Post by weaselonfire on 2008-10-13
i didnt try it with the normal install cd ever but i just finished up my install from the alternate cd, i added a line by hitting f6 and black listing that sdhci according to one of the pages i posted. The first time i tried with the alt cd i forgot to add this line and the install went through fine but the boot up would still hang on this driver.  Tried again with the new bit in that line blacklisting it and now it works.  I am posting right now from my laptop freshly running ubuntu 8.04.  Hopefully i get everything working nicely and ready to go in time to update to 8.10

---

