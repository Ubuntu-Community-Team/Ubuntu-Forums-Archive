---
title: "Upgrade problem on Sun Ultra 40"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by kkranz on 2007-04-20
Just though I'd pass this along...  Unfortunately, due to the nature of the problem, I have no debug info to post.  Absolutely new to the forum (just bothered to create an account now) and somewhat (but not  totally)  new to ubuntu.

I have tried installing 7.04  on a Sun Ultra 40.  I've tried both installing from the 7.04 CD and performing an upgrade.  In fact, I tried:

1) upgrading my existing 6.10 install, when that failed...
2) wiping the disk and doing a new 7.04 install, when that failed...
3) Installed a clean/new 6 10 OS then applied the patches via the SW manager then, finally,  performed  an upgrade.

In each case the install failed the same way - specifically:  the install seems to go well, but he system never comes back from the reboot.  I just end up in a continual reboot cycle.  

If there is a way for me to get into the system and view the error logs, I do not know about it.  I am never presented with a chance to log on or go into any maint mode.  If we think this is an ultra 40 problem and want to experiment with my machine, I am willing to donate it to the cause for a short period of time.  Just contact me and I will reserve a disk with your name on it ;-) 

Here are the specs for the machine.  In a nutshell: 
  * 2 dual core CPUs
  * 16 BG memory
  * 3 250 GB SATA drives
  * NVIDIA graphics card w/24" flat panel monitor

Details on the machine config:

Sun Ultra 40 Workstation 
1 A71-PJZ2-AP-8GB-DS
Sun Ultra 40 Workstation: 2 * AMD Opteron Model 280 (Dual-core) processors,8 GB (4 * 2 GB) DDR-400 ECC memory, 1 * 250 GB 7200 RPM SATA Disk, NVIDIA Quadro FX3500 PCI-Express graphics card, 1 * DVD Dual, 2 * 10/100/1000 Ethernet ports, 2 * x16 PCI-Express slots, 2 * x4 PCI-Express slots, 2 * legacy PCI slots, Solaris 10 Operating System Pre-Installed, RoHS-6 Compliant  
 1 X311L
Power Cord Kit, North American/Asian, RoHS Compliant  
1 X3731A
Type 7 U.S./Canada Universal PC Country Kit, RoHS-6 Compliant  
1 X7260A
4 GB (2 * 2 GB) DDR-400 ECC memory kit for Sun Ultra 40 workstation, RoHS-6 compliant  
2 XRB-ST1CE-250G7K
250 GB 7200 rpm Serial ATA Disk Drive with bracket, RoHS-6 Compliant  
1 X7203A
24.1-inch TFT LCD Color Monitor (27 inch CRT equivalent), PVA wide viewing angle, 1920x1200@60 Hz, digital DVI interface, DVI-D video cable, HD15 interface and HD15 video cable, S-video and C-video interfaces, 4-port USB hub, DVI-D, HD15, and HD15-13W3 video input cables included, Digital OSD controls, Universal Power Supply, VESA DPMS, TCO'99, WW agency compliances, Sun ID enclosure, Sun logo and color, RoHS Compliant  
1 X4184A-Z
NVIDIA Quadro FX 560 entry 3D graphics card, RoHS-6 Compliant

---

### Post by kkranz on 2007-04-21
Posting my own reply in the event it helps someone else.  I figured out that the installation was failing at the point where fiesty attempts to scan the old install for information it can import to the new environment.  To avoid this, I dropped all partitions associated with the previous 6.10 install and reran the installer.  It worked find and I now have 7.04 running w/o any issues.

Totally different note: in the process of debugging this I installed 7.04 on a Dell Precision M60 w/o any issues too.  Seems to work just fine.

---

### Post by hmv on 2007-04-23
Me too :(

I "solved" this another way by downgrading to the 6.10 kernel, and manually hacking back in the nvidia drivers to get to my current situation.

What makes you think the problems were caused by the existing disk partitions ? I *could* blow away my current partitions but I would rather not. Certainly I got far enough in the boot process that the existing filesystems were being mounted.

I was guessing that it was due to a very poorly behaved kernel module as I could leave it at the shell prompt you get with 'break=mount' for as long as I wished without the reboot happening. 

Anyone else with similar problems and solutions ?

---

### Post by kkranz on 2007-04-26
> What makes me thing it was....

Here is the path I took - remember I had a brand spanking new ultra 40, so I had nothing to lose...

1) wed, install 6.10.  Realize that 7.04 is due out tomorrow.  
2) Th, Download 7.04.  Attempt a new install - failed
3) Reinstall 6.10 and attempt upgrade - failed
4) several more attempts at this trying to debug the problem.
5) Fri, Install 7.04 on my Dell Precision M60 to verify that my download image is OK
    Realize that the install is failing at the point where it attempt to pull data out of the old install
6) Use a MS XP Server install disk to boot and drop the ubuntu partition - the best use for a windows installation disk that I can think of
7) Install 7.04 on the clean disk w/o a single hitch.

---

### Post by kkranz on 2007-04-26
I forgot one other thing.  I have (3) 250 GB disks.  I also tried installing 7.04 on the 2nd drive.  That install failed in the same manner - namely, around the time 7.04 was polling the 6.10 install

---

### Post by frieza79 on 2007-04-27
I have the same problem as you.
Everything looks the same except the Video Card.  I have an FX 4500.

At some points, I cant even get to the GRUB menu, it seems to hang on the screen where it says "press F2 for the BIOS"  That usually occurs after many self-reboots.

I have found booting to single user to be somewhat more stable. once i get in, telenit 3 works to get to GNOME.   This doesnt always work, and sometimes will just crash and I'm back to square one.

I am now running off of the older kernel from Edgy, but I have issues with the NVIDIA driver, so i reverted back to "nv" and cant use my dual monitors :-(

---

### Post by frieza79 on 2007-04-27
After reading your post again, I think you might be getting lucky on the reinstall.  I tried to reinstall with a new disk and everything seemed to work ok.  a couple of reboots later, same issues....

---

### Post by hmv on 2007-04-27
So it looks like re-installing doesn't fix the issue ? Good to hear in the sense I was going to try that tomorrow (I've got some new dsks that will give me the space to do that), and perhaps I should concentrate on blocking modules to see if that will solve things.

My U40 has slightly less memory (2Gbytes) so that probably isn't the problem. I also have an NVS285 rather than an FX*. Getting the nvidia drivers to work with the Edgy kernel isn't too bad ... you have to manually install the old kernel source debs (can't recall the name at the moment), and then use the nvidia drivers from the nvidia site, and X springs back to life (at least for me).

---

### Post by dr.modding on 2007-07-30
same problem!!  my Worsktation only had a single 250gb disk and i had tried everything... :confused: I note something funny, i can reboot the pc and ubuntu works normally  but when i  turn off just 1 minute  my workstation it´s when the problem come... if i chose Windows it delays (more than all the time.. yes it´s possible) to boot like 4-5 minutes and if i reboot my pc without turn of my pc ubuntu works again...

forgive  my english

---

### Post by dr.modding on 2007-08-11
I had reported the problem to launchpad if you had some info about this problem please send it.

[https://bugs.launchpad.net/ubuntu/+bug/131853](https://bugs.launchpad.net/ubuntu/+bug/131853)

---

