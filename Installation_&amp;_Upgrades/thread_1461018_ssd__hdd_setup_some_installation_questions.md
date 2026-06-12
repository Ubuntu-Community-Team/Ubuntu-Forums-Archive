---
title: "ssd / hdd setup: some installation questions"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by MOB_Figga on 2010-04-23
hello,

I am a 2 year ubuntu user now (ever since the intrepid ibex 7.10 version) and up until now I haven't had any regrets from changing from windows to ubuntu (linux). 

now here's my situation: I got an intel ssd (the popular x 25 v 40gb retail version), and I installed 9.10 Karmic koala on it. that ssd is placed in my shuttle sk22g2 barebone. When I try to load ubuntu from the ssd, it 'hangs' as soon as the BIOS gets to the 'Verifiying DMI Pool Data' message.. 

However, I also have an newly added 500gb samsung spinpoint f3 in my barebone. I also installed ubuntu on that normal hdd and what I noticed was, that at the restart after the install setup has finished, I got a (familiar) GRUB boot menu, which also enabled me to choose /sdb (= my ssd, which had ubuntu on it).. and then it does load ubuntu (and really fast too!).. 

I have a couple of questions concerning this:
1. Is it somehow possible for me to let my shuttle barebone load ubuntu straight from the ssd ?(I want to use my samsung hdd for data, that was my whole plan from the beginning)
2. If (1) is not possible, how should I install ubuntu on the samsung hdd  so that I have more than enough space left for my data? (it now covers all of my hdd disk space, since I always choose 'use entire disk space' ; I'm used to installing on an (empty) hdd which I would use for ubuntu only)
3. if (2) is possible, how can I, when I get to the Desktop, always get to the free space that I want to use for my data. and by ´always' I mean: just like the standard 'places' that you can choose from in the places menu, without having to 'authorise' myself each time (obviously I have to format that part of the disk, but I haven't done that before, manually)
4. if (2) is possible, could I adjust/rearrange the options in the menu so that automatically my ssd is selected to boot from? and can I decrease the number of seconds that GRUB allows me to react by pressing a button, so that startup time decreases (even more)?


can someone help me with this?

---

### Post by MOB_Figga on 2010-04-27
nobody wants to help :( ?

---

### Post by Drenriza on 2010-04-27
I dont rly know how to tackle this problem off the bat.
 
What happends if you disconnect your 500gb drive. And only has the ssd drive in your computer? does it then boot directly from the ssd.
 
In your bios, cant you set the ssd as the systems primary disk, and the 500gb drive as the systems secondary disk.
 
 
What i dont rly get is, if you only have installed the filesystem (primary) partition on the ssd, and an extended (formatted partition) on the 500gb. And installed ubuntu on the ssd. Why doesnt it then just boot directly from the ssd.
 
I find it abit strange. Does the kernel even support ssd disks as it is atm? i cant rly find the ssd in the HCL list.

---

### Post by MOB_Figga on 2010-04-30
k, maybe I need to clear up some misunderstandings:

- I have installed ubuntu 9.10 on the ssd, and it has al the partitions (extended, swap etc) on the ssd itself (I chose 'guided use entire disk')
- then, when I wanted to startup from the ssd, that is: after the installation, ubuntu will tell me to get the cd out before the restart and press a key (which I did). then, I could see my splash screen from shuttle, then the 'verifiying DMI pool data'  (which always comes before the ubuntu load screen), but after that the system hung up on me (also after some 'hard resets')

NOTE: In the BIOS, I could see the ssd in the attached disk drives (so my BIOS indeed detected it) and yes, I had setup the ssd as the primary disk drive to boot from

- since it wasn't working like I wanted it (as described above), I repeated the installation on the hdd (also choosing 'guided use entire disk') and after I restarted, I got the GRUB menu, which also listed my ssd (actually ubuntu, kernel bla bla, /sdb1, which is my ssd)
- Now, I could load further (and fast) ubuntu

maybe this clears things up, I'm sorry if this was somewhat unclear at first

---

### Post by choices111 on 2010-05-19
i had the exact problem, but with 10.04...so what i did was i installed it again & i noticed an advanced button on 1 of the screens(sorry cant remember which 1 & forgive me for being very vague)...i entered the advanced button & chose where i wanted to save the boot loader & i chose the ssd

---

### Post by Perka on 2011-01-06
Hi, 

I just got some similar problem.
I decided to upgrade from my old USB-stick I used as root system to a new SSD (OCZ Agility 40GB).
All the installation went fine.. Boot from Ubuntu server 10.4 on USB-stick and installed it to my SSD.

But after it said that I should remove media and restart to get into my new installed system it got stuck at DMI pool data..
Now the only way to get the system up at all, is by using the old USB-drive again and disconnect the SSD.. 

I installed GRUB on MBR on my SSD the first time so I'm wondering if I  need to clear this part to get back to how I had it before when I could  boot with the SSD connected.
Does anyone got any idea how I could perform a new install and try to find the advanced settings for GRUB?

Is it possible to attach the SSD while my system is up and running? After '..DMI pool..'
Anything I should think about if I would give it a try?

---

### Post by Perka on 2011-02-09
Ok,

Now I had some time to go over this again.
I had to do a hirens boot cd with my SSD disconnected, once I got to its menu I connected the SSD again and choose to boot mini linux. (there seems like my motherboards boot-priority is also was a bit strange, resulting in that it never tried to boot USB once it tried with the SSD)
I then wiped everything and started over with the Ubuntu install.

It seems as I also had the same problem with installing grub.
When the installer asked if I wanted to put GRUB on MBR I said yes, and in the busy "executing command" screen that just appears for a brief moment I saw that it tried to install it on /dev/sda.
The problem was that my SSD was /dev/sdb and the install-USB was /dev/sda :(

So instead of restarting once the install was complete I went back to MBR installation and chose NOT to install it on MBR, then in the next screen I was able to install it on /dev/sdb instead.

Now its up and runnning

---

