---
title: "Maverick Meerkat boots slow and desktop enviroment laggy"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by dre1187 on 2010-10-12
Good afternoon all, 

I am at a loss on what to try next. Here is my issue:

from the time that the boot process begins to get to the Ubuntu log in screen it takes about 3 minutes. Sometimes it will switch back and forth from the purple screen to terminal. After I hit log in it takes around 1-2 minutes for the desktop environment to load and be usable. Once its loaded apps take around 30secs-1min to load. 

On the 10.10 install I aligned the SSD using fdisk -H 32 -S 32, and then created 2 partitions 300mb /boot and the remainder was for /. I formatted /boot to be ext2 and / to be ext4. Also i selected the option to encrypt my home folder.  

Before the 10.10 install I was running 10.04 with this set up and it was extremely fast, even though I did not align the SSD using the default fdisk -H 255 -S 63(or something along those lines). On this install my home folder was not excrypted.

My set up:
Asus P5Q-LE MOBO 
4gbs of DDR2 Ram
Intel Core2Quad 6600
OCZ Agility2 60gb HD Firmware Version 1.10 (used to /boot(ext2) and /(ext4))
WD Caviar Green 500GB (/home(ext4))
WD Caviar Black 1TB(/storage(ext4))
WD Caviar Green 1.5TB(/storage2(ext4))

On the OCZ forums they suggested to do a secure erase, then reinstalling. I thought that since the whole disk got re-partitioned i wouldn't have to use erase the drive as it was done already with the partitioning. 

your thoughts and ideas on what to do would be greatly appreciated. 


thanks,

---

### Post by dre1187 on 2010-10-12
okay so after much testing i have arrived at the conclusion that 10.10 kernel 2.6.35 is the problem. I think it has to do with how kernel is treating the OCZ Agility2 SSD. 

I tried to:
-install 32bit 10.10 on aligned disks with options for 3rd party and updates selected. After doing secure erase. outcome doesnt boot gets IRQ19 message and blinking _

-install 64bit 10.10 on both aligned and not aligned disks with option for updates and 3rd party software checked and not checked. Outcome doesnt boot and get IRQ19 message along with blinking_

Finally i re-installed 10.04.1 64bit using 2.6.32 kernel and everything installs and runs lighting fast. 

If anyone has any ideas or thoughts on how to get 2.6.35 working it would be greatly appreciated. I am in need of utouch and TRIM .

thanks again

---

### Post by LordMephisto on 2010-10-13
Hello,

I have a very similar problem with Ubuntu 10.10 (x64), but with a completely different hardware setup. I have:

2x Intel Xeon E5540 (Bloomfield 4 Cores, HT, Turbomode active)
2x Seagate 500 GB
16 GB RAM (2x 4 GByte per socket)

The boot processes is extremely slow using the new 2.6.35 kernel. Using the old 2.6.32 everything is fine.

Because I have no idea where the origin of the problem is located, I attached a file containing the complete log file created during the boot process. Maybe some of you have an idea ;)

Thanks in advance
Lord

---

### Post by stockham on 2010-10-14
I too have had this issue. I can use older kernels (2.6.32) with no issues. I did find a work around. I actually hit the power button which sends a interrupt signal to the ICH, this triggers the load sequence and it will eventually boot. A couple time I would get the initramfs shell and I would usually just "exit" to resume booting. I know this is a clunky way to boot up but it is what I have so far...I will update when I find out more.

---

### Post by dre1187 on 2010-10-14
@ stockham

I will try to reinstall the 2.6.35 on my 10.04.1 install as well as the 2.6.36rc on here as well and try your trick out in a couple days...Im hoping someone will figure out the fix.

---

### Post by stockham on 2010-10-15
> **dre1187 said:**
> @ stockham

I will try to reinstall the 2.6.35 on my 10.04.1 install as well as the 2.6.36rc on here as well and try your trick out in a couple days...Im hoping someone will figure out the fix.

I am running a new designed Tablet with an Atom N450 processor, ICH8, Embedded Graphics, 2G DDR2, mSATA SSD and a 1.8" MicroSATA with Win 7. When I try and run in recovery mode, it seems to hang in a different spot each time. I have not yet tried the new kernel (2.6.36rc) but maybe it will have different results. I did not have this problem with 10.04 NBR and the 2.6.32 kernel.
Let me know how it goes with your tries..
Once I get it to boot up, it seems to work great and fast. I loaded a couple different Desktop Environments to play a little. KDE with Plasma is pretty cool, Xfe and Xubuntu are really fast, clean and light weight. If I didn't have to deal with MS Office and Exchange, I would completely dump Windows. Although Win 7 seems to be the best MS OS by far...

---

### Post by joxl on 2010-10-20
Same problem here.  I'm really at a loss.  Here's my setup:

Ubuntu: 10.10 GNOME Desktop
Kernel: 2.6.35-22-generic (x86_64)

MOBO: EVGA 132-BL-E758-A1 X58 3-Way SLI
CPU: Intel Core i7 920 2.66GHz (quad core)
RAM: 6GB (3 x 2GB) DDR3 SDRAM
GPU: XFX Radeon HD 4650 - 1GB DDR2
HDD: /dev/sda1 (/) ext3: Seagate Barracuda 7200.11 1 TB SATA
HDD: /dev/sdb1 (/media/Archive) ext3: Seagate Barracuda 7200.11 1.5TB SATA

I just upgraded to Maverick today.  Well to be honest, I started the upgrade yesterday through the "Update Manager".  The upgrade failed (haven't had time to report that yet) and my machine crashed in a very unstable state.  Upon reboot, the root device (/dev/sda1) had errors, I chose to "attempt to fix automatically" or whatever the option was.  After that the GUI would not load, but I was able to SSH in from a remote machine on the LAN.  From there I ran apt-get manually and completed the upgrade.

Finally, a "clean" upgrade, next I rebooted the machine.  It took about 15-30 minutes until I finally reached the login screen.  During this eternity, the screen would flicker in/out of the purple "Ubuntu 10.10" screen and *blank*.  The monitor often went to sleep due to inactivity.  The GUI was very laggy and took about 5 minutes to log in.  After finally getting logged in the machine continued to lag and periodically hang.  "System Monitor" reported near max CPU usage, but I could not identify the culprit process(es).

So I rebooted again.  This time the login screen loaded as quickly as I would expect (around 30 seconds).  But upon logging into the GUI, the excessive CPU usage began once again rendering the session nearly useless.

OK, time to start hacking.  SSH'd in from the remote machine, here are the tools I found most helpful in tracking down "rogue" processes:

htop
ps
pstree
initctl
service

What baffles me is that the CPU usage reported by htop and ps never seemed to add up to the amount displayed on the htop graph.  That could just be inaccurate reporting, but I found it strange.  There were a few services with (what I think) *far too many* processes running, however I couldn't really pin the blame on those services.  When snooping with htop, the main X process was always eating the most CPU, so I shut it down.

```
# make sure you're logged out of the GUI before you try this,
# --or-- at least save your work.  In any case I wouldn't recommend
# trying it from terminal in the GUI.

sudo initctl stop gdm
```It took about 2 minutes for gdm to quit, and things were still slow when it finally did.  After waiting a little while though (5 min?) the excessive CPU usage seemed to disappear.  Of course I got my hopes up too soon, over time I noticed the CPU fluctuate up and down drastically.  In any case, it seems the behavior is constant while gdm is up, but only periodic while gdm's down.

Any more help on resolving this would be great.  I'd like to start using the GUI again one of these days ;)  Thanks in advance!

---

### Post by Kyllerss on 2010-10-22
I am experiencing the same issues. You might want to check these out:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/664877](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/664877)

and 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/662946](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/662946)

So far no fix, but at least someone is looking into it. The latter bug report states that going to 2.6.36 supposedly fixes the issue.

---

### Post by The__Doctor on 2010-11-02
I found using 10.10 on kernel 2.6.32 worked fine. I had lag on 2.6.35, and even on 2.6.36, but when I switched back to 2.6.32, everything ran quite smoothly.

---

### Post by Scott Deagan on 2010-11-08
@[The__Doctor]("http://ubuntuforums.org/member.php?u=1008800") - how did you install a 2.6.32 kernel? I'm running 2.6.35 on a Sony Vaio VPCF11S1E/B and it's very slow and sluggish. I also had a problem with my nVidia drivers so thought that this was the problem (can't yet install a 260.xx nVidia driver on an Vaio F-Series). However, after digging around it seems many others are experiencing the same slow and sluggish/laggy performance issues.

---

### Post by prmcafee on 2010-11-09
I was experiencing quite a lag with kernel 2.6.35 on 10.10.  I just went through the 2 links posted a couple of replies above, and updated to 2.6.37 and so far my lag has disappeared.  I was also having a video problem in GDM where the graphics were distorted.  I was still able to log in but the video would distort.  That seems to have disappeared.  Now I just have to get my desktop to load up more efficiently.  Any tips here would be greatly appreciated.  Don't worry, I'll also be using the search function through the forums.  :)

---

### Post by stockham on 2011-02-02
> **prmcafee said:**
> I was experiencing quite a lag with kernel 2.6.35 on 10.10.  I just went through the 2 links posted a couple of replies above, and updated to 2.6.37 and so far my lag has disappeared.  I was also having a video problem in GDM where the graphics were distorted.  I was still able to log in but the video would distort.  That seems to have disappeared.  Now I just have to get my desktop to load up more efficiently.  Any tips here would be greatly appreciated.  Don't worry, I'll also be using the search function through the forums.  :)

Where did you find 2.6.37? It seems the latest release is 2.6.35-26.

---

### Post by davidmohammed on 2011-02-02
at a guess I reckon the poster downloaded the latest "maverick" kernel from [here]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds")

---

