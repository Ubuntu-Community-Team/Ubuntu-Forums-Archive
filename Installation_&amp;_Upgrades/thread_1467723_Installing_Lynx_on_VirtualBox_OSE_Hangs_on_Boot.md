---
title: "Installing Lynx on VirtualBox OSE Hangs on Boot"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by angheloko on 2010-05-01
Hi All,  I am planning on playing with the lynx on VirtualBox for a while just to do some test and maybe update my installation notes before moving everything but just can't get it to work. 

Environment details: 
  OS: 9.10   
Kernel: 2.6.31-21-generic 
  Machine: Compaq Presario B1200, 3 GB RAM, 14 GB available disk space
VirtualBox: VirtualBox OSE 3.0.8_OSE r53138 
     
Problem: 
After starting up the virtual machine and reaching the purple screen (where a keyboard and accessibility icons are displayed at the bottom part), everything just goes black with an un-blinking cursor on the top-right. 

I already tried recreating the virtual machine, removing and creating a number of times, and I've also tried reinstalling VirtualBox but the problem still persists. 

Anyone encountered this before? Any help is greatly appreciated.

---

### Post by angheloko on 2010-05-01
Brainfarts! It's alive. 

I guess it's just me and my impatience. My li'l ol' slow friend here decided to take his time doing his processing. Anyway, after 5 mins or so, or just after preparing myself some nuggets, lo and behold, the purple fiend awaits my login.

---

### Post by caseyboardman on 2010-05-01
I'm seeing similar behavior.  Disabling ACPI seems to speed things up. (Per [http://forums.virtualbox.org/viewtopic.php?f=3&t=27416](http://forums.virtualbox.org/viewtopic.php?f=3&t=27416)).  I'm installing now.

I am running the same version of Virtual Box OSE, but on Kubuntu 9.10.

---

### Post by angheloko on 2010-05-01
Hi Casey,

Actually I am experiencing excruciating slowness and unresponsiveness  but after disabling ACPI like you said, everything speeded up like normal.

I've reinstalled and is testing now.

Thanks for the info!

---

### Post by alienprdkt on 2010-05-14
> **caseyboardman said:**
> I'm seeing similar behavior.  Disabling ACPI seems to speed things up. (Per [http://forums.virtualbox.org/viewtopic.php?f=3&t=27416](http://forums.virtualbox.org/viewtopic.php?f=3&t=27416)).  I'm installing now.

I am running the same version of Virtual Box OSE, but on Kubuntu 9.10.

Thanks for the fix!:P

---

