---
title: "ubuntu freezes after two minutes. /Dual boot with windows 7"
date: 2011-08-17
forum: Installation &amp; Upgrades
---

### Post by suicidalandroid on 2011-08-17
Sorry if I jumped the gun a little bit here, and posted this before completly filing over every other thread. But, I haven't been able to find anything really relating to my problem. 
I have windows 7 installed. 32bit. I've decided to setup a dual boot with this and Ubuntu. Specifically version 10.04. I've gotten it all to work out relatively well. I installed ubuntu on it's own seperate partition. Set up a swap partition as well. Restart. Boot back up into windows. I used EasyBCD because I decided to leave GRUB2 on the ubuntu partition. So, I set up the windows boot manager so it now sees and acknowledges Ubuntu. Restart the system again, and the boot manager comes up. Select Ubuntu. Go into grub menu, and select ubuntu again. Loads like normal. I get to the log on screen, log in, and start running around Ubuntu. Within two to three minutes, Ubuntu freezes up. No key commands, or anything. The power button doesn't even work. I have to hard reboot the whole computer. well, unplug the power cord.. if theres a difference. Any ideas on why this is happening? I'm completly new to the whole ubuntu experience.
 
On a side note, when I installed Ubuntu, after it was all done, it asks to reboot the system. So I click ok. When I do that, right before it completes the reboot, a whole bunch of lines of code come up, saying something about some kind of error. I didn't really remember what it all said.. Just that the ending numbers in each line went up in increments of 8.
I installed it with the .iso, if that helps anybodies answers. I also tried to reinstall it, figguring that something was just corrupt with the cd I burned. But, the same exact things happened.

---

### Post by valantis on 2011-08-17
> **suicidalandroid said:**
> Sorry if I jumped the gun a little bit here, and posted this before completly filing over every other thread. But, I haven't been able to find anything really relating to my problem. 
I have windows 7 installed. 32bit. I've decided to setup a dual boot with this and Ubuntu. Specifically version 10.04. I've gotten it all to work out relatively well. I installed ubuntu on it's own seperate partition. Set up a swap partition as well. Restart. Boot back up into windows. I used EasyBCD because I decided to leave GRUB2 on the ubuntu partition. So, I set up the windows boot manager so it now sees and acknowledges Ubuntu. Restart the system again, and the boot manager comes up. Select Ubuntu. Go into grub menu, and select ubuntu again. Loads like normal. I get to the log on screen, log in, and start running around Ubuntu. Within two to three minutes, Ubuntu freezes up. No key commands, or anything. The power button doesn't even work. I have to hard reboot the whole computer. well, unplug the power cord.. if theres a difference. Any ideas on why this is happening? I'm completly new to the whole ubuntu experience.
 
On a side note, when I installed Ubuntu, after it was all done, it asks to reboot the system. So I click ok. When I do that, right before it completes the reboot, a whole bunch of lines of code come up, saying something about some kind of error. I didn't really remember what it all said.. Just that the ending numbers in each line went up in increments of 8.
I installed it with the .iso, if that helps anybodies answers. I also tried to reinstall it, figguring that something was just corrupt with the cd I burned. But, the same exact things happened.
Hi just  boot on windows delete the ubuntu partition and make a resize the windows patrition to take all your disk. boot from live cd then ubuntu it ask you how many space you want to give it just mark the space tha you want for linux and click it to install .give the oportunity ubuntu deside how and what it make to have a good installation. the error that you can see at start up it does't mean tha is something really importand but you must see if you make a mistake in partitions.

---

### Post by suicidalandroid on 2011-08-18
Ok, so I've been back, in and out of ubuntu a few times now. All with different results. One time, I was able to read some system logs, sadly, most of it doesn't really mean much to me yet, buut, I plan to change that very soon. After reading things, and wondering what exactly it means, everything still seemed fine now, so I ran the update program, and proceeded to download. Restared the computer, and booted back into ubuntu. I checked out mouse settings, wondering if that had something to do with it. I've seen a lot of threads and posts saying the keyboard/mouse freeze up, and it's not the actual os, but they still have to reboot. Didn't help. I forget what else I looked up, but I went to the help button, and it opened up firefox, and then it froze again. I decided to reboot it again, and try to wander around the programs and stuff for a little while. Everything worked fine, and then I went out for a little while. Came back, woke the computer up, had to log back in, everything worked for a minute or two, and then froze up, yet again. It doesn't even seem connected, really. Each incident. I'm going to try to get some pics up soon. When I was reading the logs, even I saw some stuff that didn't look right. Missing programs, and a few other weird things.
 
@valantis Is it really better to use grub2 as the main boot manager? The things I've read about useing it instead of the windows one are 50/50 really. And the thing about the error at the end of the reboot right after installing it, does that mean that I messed up on making the partitions? I ended up, when it asks you where you want to install ubuntu, I went to the last option, where you choose the partitions for it. I have a 3gb primary partition, for swap, and a 59gb extended partition for ubuntu itself. The first two partitions are windows. That little 100mb one, and windows itself.

---

