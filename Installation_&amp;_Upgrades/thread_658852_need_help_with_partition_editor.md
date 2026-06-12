---
title: "need help with partition editor"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by Irti on 2008-01-05
hey......i am a new linux user and wanted to install 7.10 on my pc.....i have a 160 gb hard drive with 2 partitions c and d.........i wanted to install 7.10 on my d drive on a 15 gb partition......so when the partition editor pops up while installing i tried to specify 15360 (at it says that i have to specify the new partition size in mb) but then the a message comes on saying that the partition size is too small.....i wanted to know if i have to specify the partition size to resize my existing d drive or am i specifying the partition size for my new ubuntu partition...??? plzzzz help

---

### Post by mikewhatever on 2008-01-05
You have to resize one of the existing partitions first and then specify the sizes, or let the installer do the job. [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
It's a good idea to defragment the partition before resizing.

---

### Post by Irti on 2008-01-05
ok.....i made a major mistake.......i set up the partition size for my ubuntu partition properly....but then accidently i set up the remaining space on the windows partition as swap...i cancelled it before the whole thing could actually finish but then the damage was already done..i tried the " undo changes to partition" but nothing is working......the drive has disappeared from windows and my linux live cd is not loading up...it shows up thru the computer management utlity in windows......but i cant access anything on it....i dont even know if the drive has been erased as it just shows 80 gb (healthy)....pls help.....i want to undo all the changes...and recover the data on my drive back.........plzz help

---

### Post by ubutufan on 2008-01-05
Not sure I understand what the problem is.
Are you booting into windows? If yes what is it that you cannot access?
Please be calm and try to give clear info

---

### Post by c0met on 2008-01-05
I assume that you have checked the boot-up sequence in your BIOS. If that is set so that the BIOS boot-up preference is for the CD drive as the first boot, then the only reason  that I can think for the LiveCD's not booting is that CD drive is not reading it. The LiveCD boot is not affected at all by what software you have on the computer. That it doesn't boot, suggests that it might be wise to burn a new LiveCD. 

One thing that I have picked up from these forums is that it is often wiser to burn CDs at a significantly lower speed than your maximum burning speed. This helps to guarantee the integrity of the file system when its written to the CD.

---

### Post by Irti on 2008-01-05
ok.....lets see...the problem is that while setting up ubuntu i managed to partition my drive properly to set up a 15 gb partition for ubuntu...but while setting up swap space...by mistake i set up the whole of the d drive as swap.....i cancelled it before the whole process could actually go through...but now my d drive has just disappeared...as in i cannot see it thru windows or when booting from the ubuntu live cd.....and after i restarted i tried booting through ubuntu live cd but it just shows up a lot of errors......i had a lot of data on the d rive and i was wondering if there was someway i could get the d drive working again.....the drive is set up as swap but i dont think the data is erased.....i want to convert it back to ntfs again and if possible restore the data........

---

### Post by c0met on 2008-01-06
Hi,

If you boot from the LiveCD, you can run a program under System >> Administration called GParted. This is a partition editor/creator program. More importantly for you, though, is that it will let you see how your partitions have been processed because it will provide information on format and size. This is all done graphically. Find out what this says.

At this stage, it would be wise not to try and re-format any of your partitions until you have a bit more information.

c0met

---

### Post by HW_Hack on 2008-01-06
Yes ---- keep this very simple use the Gparted tool on the Ubuntu Lice Cd --- your only goal is to create an empty space for Ubuntu to get loaded on to. You do not have to worry about swap space or making partitions --- just use Gparted to delete what was your old D: drive space (if thats what you are doing).

Then during install when you get to the drive partitioning choice --- all you have to choose is Guided Partitioning (Use the Largest area of Free Space) and Ubuntu will install itself and setup a GRUB boot manager so you can dual boot. 

Good luck

---

### Post by Partyboi2 on 2008-01-06
When you say
>  i tried booting through ubuntu live cd but it just shows up a lot of errors
>  and my linux live cd is not loading up
Are you saying that you can not get to the desktop to be able to use gparted?
If that is the case you can download gparted as a live cd
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

