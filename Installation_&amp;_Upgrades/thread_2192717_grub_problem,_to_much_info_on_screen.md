---
title: "grub problem, to much info on screen"
date: 2013-12-09
forum: Installation &amp; Upgrades
---

### Post by goodbye-windows(tm) on 2013-12-09
Hi All,

I have to do a quad boot system to do some experimenting. I have installed all 4 partitions. Two of them are 12.04 unity and 13.10 unity. The other two are 13.10 unity and 13.10 xubuntu. All 4 of the installs are 64 bit versions.

Somehow, something caused the grub screen to become very large, with data from each line scrolling off the right hand side of the screen. When grub runs, the output doesn't tell me much as much of the data scrools off the screen on the right hand side. I can't tell which line opens which partitions!!!! I wish I could do a screen capture...but I'm not sure it's possible without a gui running.

All 4 partitions show on gparted, and there were no (visible) errors during any of the installs. 

I tried sudo grub-update, but it made no difference. During the grub update, the text on the screen showed that it had found a total of 4 operating systems on 4 different partitions. 

My computer is a Dell 15R with an I5 processor. It had been running well until I decided to do some experimenting with a multiboot system. 

Does anyone have any idea what's going on, and how to fix it??

TIA

Art

---

### Post by Bashing-om on 2013-12-09
goodbye-windows(tm); Hello ,

I too run a multi-boot box. I found that my grub menu became unwieldy and difficult to manage with so many systems and kernels to boot. 
Cavsfan has a good solution, as well as setting grub's resolution.
See:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

One does, however, on occasion have to (re-)install grub when the current boot procedure is disrupted - no big deal.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by Dennis N on 2013-12-09
[I]"Does anyone have any idea what's going on, and how to fix it??"
[/I]
Yes. What version of Grub is generating your grub menu, 1.99 or 2.00? You can read this off the top of the grub menu screen.

---

### Post by oldfred on 2013-12-09
With 4 installs, all 4 may try to update grub2's boot manager in the MBR. You want one to be in control and that one should be the one you boot the most. And then it will also be first in grub menu.
I also turn off os-prober  in all installs and use my own 40_custom for all added installs using Cavsfan's partition boot type boot stanza.

On the other three undo grub update.
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)
You may be able to unchoose everything or select a partition which is not normally recommended, but just as a throw away, so that install does not update MBR.

Your issue is probably a default grub video of 640x480 or similar setting. Usually grub now tries to use video from install. The version in control now probably has some sort of video issue or settings in /etc/default/grub.

---

### Post by goodbye-windows(tm) on 2013-12-13
Thanks to all who replied. I am going to mark this one as solved. 

What I discovered is that the default screen for grub ver 1.99 has a bunch of output data that most users don't need. But, grub 2.0 has the short version which is much more human friendly.

I didn't actually figure out how to convert grub 1.99 to grub 2.0, but the problem went away once I stopped trying to use older version of xubuntu.

Again, ty to all.

Art

---

### Post by PopsTheSailor on 2014-01-12
> **oldfred said:**
> 

On the other three undo grub update.
 

I'm having a similar issue with 3 installs of Linux and 1 for Win 7. Could you explain what you mean / how to "undo grub update"? It sounds like this is a way to remove the grub info off of the installs that aren't the primary one I use.

---

### Post by oldfred on 2014-01-13
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

      
 In /etc/default/grub I added this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub
But then it will not find other systems at all.

 Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

And you can house clean kernels.
      
 Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

