---
title: "Can't re-install, and boot loader is dead"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by JonathanSchroeder on 2008-07-07
Ok, so I have quite the happy story that ends in having a computer with a dead grub and the inability to install ubuntu with cds that i know are good.

So I had 2 hard drive, one with windows and one with ubuntu, but i got a bigger one so i decided to replace my ubuntu one with it, and use my old one later for an old pc of mine. So I transfer the data over. Its all good and happy. As a note here, i would like to say that a while ago I put root on a separate partition from home, so the majority of my data would be safe whenever i killed my root. However now that i had my 500GB hard drive, i decided i wanted to also back up root. So I added another partition for that.

Now I have been running 7.10 for a while, cus 8.04 has always given my graphics card problems, making me run in low resolution with no special effects. I decided to hope it was just cus i had installed bad things, so I reinstalled ubuntu. Now here is where the red flags should have been going off, cus when the boot loader starts, now their are like 3 coppies of the same ubuntu to start from (below the 1st set of ubuntu and XP their are 2 other sets of ubuntu that have stuff like this (hd1/hda) next to them to signify which partition. Note, that was just meant as an example, i don't know what the actual thing said.

Before upgrading to 8.04 I first install all the very important programs to have, and update my os. This includes installing azureus (bittorrent program). Now i decide to try and solve my NAT errors, and try to foward the ports. This involves adding a file to /etc/init.d/  and info on it can be found here [http://www.azureuswiki.com/index.php/NAT_problem](http://www.azureuswiki.com/index.php/NAT_problem) . Now i am stupid, and I accadently delete the /etc/init.d/ folder. Yeah. However my old os is backed up, so i copy that folder onto this hard drive, and hope i didn't kill it.

Finally, I back up root, using a command in the terminal i found on a site. If absolutely necesary i *should* be able to find it agin, but it basicly had me tar all my folders in root except ones like home and media, and it archived them in root.

Now i upgrade to 8.04, and it won't load the os. It has errors right before it should, and things fail. I can't check what, cus i cant' even get there any more, but in the end, i just have a command prompt, and since i am not a god of this, i shut down the computer, and try and reinstall 7.04. This is where i start getting install problems. I now find that partition editor is crashing a lot, and so is the installer when i click continue after i set up the partitions as /home and /root

I have the cd image still and its good, so i make a new cd, and it still fails a few times, but i eventually get it to go past that somehow, but now it keeps on freezing at 88% when it is trying to import documents and settings. I don't know where it would import them from, it didn't ask me about it. It does nothing, no mater how long i wait. So i x out of it, and try an 8.04 cd. Same thing. Now i am sad, and decide to just calm down, wait and think. I try to load my windows os, but the boot loader is shot.

I had backed up everything onto that old hard drive, but when i put it back in my computer, it said all the space was unallocated. I tried to then copy stuff to it, but it needs a label, and partition manager crashes when it tries to give it one.

I have downloaded a kubuntu cd in case that may help, butI really like ubuntu if i can keep it. I know this may seam like a giant mess of stupidity, but i would GREATLY apreciate any help that can be given. If at all possible, i would like to keep the data on my home partition. A lot of important stuff is on there. Though i supose if i had to, i could just save what ABSOLUTELY had to be saved.

---

### Post by warpuck on 2008-07-07
If the grub boot disk didnt work try using Zenwalk live cd Gparted usally reads partition info. If it can read the drive you may be able to tranfer data to a cd or dvd using K3b on the Zenwalk cd. I am not good with command line recovery in Linux. i have found online help to do cookbook recovery using sudo. Some things can be recovered using sudo in terminal with that disk. 
 
Last resort
I have recovered disks but not the data with MaxBlast or Seagate harddrive utilility. if the drive got messed up I usually just zero them now. i ahve also learned to make 2 dvd or cd copy of things I want to save off the hardrive, I have yet to figure out how to shortcut putting all the things I llke back in. Some times I have to screw up the system so I dont forget how to fix it. maybe that is the Windows advantage.
:lolflag:

---

### Post by JonathanSchroeder on 2008-07-07
ah yes, the windows advantage: you DON'T have to kill your system a 100 times before you master it. I still prefer the ubuntu though, even if it does kill me sometimes!

Well, i will try that zenwalk cd. Will have to wait a number of hours till my mom returns with her labtop though, so that i can burn the cd. As a note though, i have already downloaded a kubuntu cd onto my mom's labtop, so wichever works is fine with me!  Also, i have a 4 gig flash drive. This make me really really happy right now, cus i don't have 2 cd/dvd drives, so i would not be able to use the method of copying stuff to a DVD. Once i am using it though i will say if i can read it, and maybe we can go from there with a terminal command. Hay, can you restore grub with a terminal command? Cus if so, then i could go to my windows and start that zenwalk cd sooner.

---

### Post by JonathanSchroeder on 2008-07-08
Ok, so i tried the zenwalk cd, but it went crazy once the live cd booted, so i decided to try the kubuntu cd, and as luck would have it, it worked. Not sure how or why, but it did. I wonder if it was maybe cus i added a /boot partition... So yeah, boot loader is living again, and kubuntu has replaced ubuntu...I wonder how long it will be till i kill it again? lol.

---

