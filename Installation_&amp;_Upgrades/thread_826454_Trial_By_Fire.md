---
title: "Trial By Fire"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by jarvis1023 on 2008-06-11
TRIAL BY FIRE

I am an experienced computer user.  I work as a network administrator for a windows network.  I decided I wanted to learn about Linux.  This is the story of my experiences with my first Ubuntu installation.

I have a 40 gig hard drive on a laptop.  I downloaded the live CD from the Ubuntu website.  This CD essentially did nothing when I booted from it.  I would get to the menu but any of the installation options did nothing.  

Then I went back into Windows XP on the harddrive and found the program called WUBI.  I read about how it was used and installed a 15 gig section for Ubuntu using WUBI.  Everything worked fine except now I was left with a 15 gig installation of Ubuntu.

Next I wanted to make the laptop Ubuntu only.  I leared of LVPM and partition manager.  partition manager was supposed to be able to break up my partition.  It was not able to do so.  I then went back into windows, erased many of the files after offloading htem to and external USB.  I ran Partition Manager but made a fatal mistake in creating the ex3 and linux-sap partitons as logical partitions.  

I reloaded the computer into Ubuntu and decided to removed the windows partition.  I was going to then resize the linux partiton to fill the remaining space but when I rebooted the computer I realized what I had done and was left with essentially no operating system.

Luckily I have other computers and I was able to obtain 2 other pieces of software GPARTED and SUPERGRUB.  I burned both of these to CDs as bootable CDS.  I first used GPARTED to copy the LVPM copy of linux that was in the logical partition to the unallocated area at the begining of the HD.  This made a copy of my Ubuntu in sda1.  I then erased the logical partitions I had created.  I then resized the partition to fill all but hte last 2 gigs of the HD where I created a second partition for the linux-swap.

With fingers crossed I rebooted the laptop.  Nope there was now no Grub at all and I was gettign the error 22.  Fortunately I had anticipated this problem and loaded SuperGrub on its bootable CD.  This program was able to recreate a grub for me.  This was not the end of my problems as I'm sure the experienced users are already seeing.

The next thing is the fact that when I choose and of hte options it gave me an error and dropped to a bustbox command prompt.  Once again I surfed for answers and found that the problem was in the fact that the UUID had changed sinceI had messed with the partitions.  I found htat there is an older way of summoning hte kernal portion and replaced the UUID information with /dev/sda1.  This was gettign closer but still didnt work because there was alot of extra parameters left over from the WUBI install.  I removed the extra information on the root hd(0,0) and took out the loop portion in the kernal line as well as the splash so I could see what was going on.  This didn't happen all at once as I tried different variations until Ubuntu came back up.

Of course this is only a temporary solution so I still neded to use the gksudo gedit /boot/grub/menu.lst file to make my alterations permanent.  I then rebooted and downloaded a few updates.  I'm not sure if my jorney is over but I'm writing this in the text editor in Ubuntu so everything appears to be working correctly.  

I was at times frustrated and at times angry but I learned alot and its a great feelign of accomplishment to make something work like this.  I have the highest of hopes for Ubuntu and its features as I learn more and dig into the many and varied aspects of the OS.

---

### Post by Pumalite on 2008-06-11
Welcome to the club.

---

