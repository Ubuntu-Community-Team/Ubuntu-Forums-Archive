---
title: "Issues loading up installer."
date: 2018-12-01
forum: Installation &amp; Upgrades
---

### Post by sufojareth on 2018-12-01
Hello I am trying to install the current LTS version of Ubuntu on an old laptop. I am trying to install from a DVD as I cannot get this laptop to pickup any USB drive that I've made into a bootable drive. I am getting ACPI errors when it first loads. It will load into an Ubuntu splash screen and then a ton of other errors pop up. I do not know how I could take a proper screenshot from the BIOS but I took some pictures from my phone which I'll attack to this post.  Any help is appreciated.

Here are my laptops specs:
```

System Manufacturer: Sony Corporation             
System Model: VGN-CR220E                     
BIOS: Ver 1.00PARTTBL                
Processor: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz (2 CPUs), ~2.0GHz                  
Memory: 3072MB RAM
Chipset: Mobile Intel® 965 Express Chipset Family

```

ISO used : ubuntu-18.04.1-desktop-amd64

---

### Post by kc1di on 2018-12-02
Sony's of that era are sometimes hard to get going. Ubuntu may not be the right choice if it's a stock machine they came with only 2 GB ram which though Ubuntu's gnome desktop may run on it would be very sluggish.  I would recommend xubuntu or Lubuntu for that machine. Does this machine have a 32 or 64 bit processor?

---

### Post by sufojareth on 2018-12-03
The machine has a 64 bit processor. I also have 3 GB of RAM in the machine if that makes a difference,

 I ended up getting Ubuntu to install last night. I just let it sit for a while and it eventually started. The system seems to be hanging frequently though. Has a really long boot time as well. At least 3-4 minutes. When booting from recovery none of these issues are present. I see a logs application but am not sure what would be helpful to post from it nor was I able to interpret what most of the errors meant myself. There seemed to be quite a lot going on in the logs though. Quite new to using a Linux distro sorry.

---

### Post by sufojareth on 2018-12-03
Okay so the system hangs when doing a normal boot are everywhere. Basically any time I load a program the entire system hangs until it is fully loaded. I haven't tried too many apps yet but all of these caused a system hang of at least one minute: Settings, Firefox, Steam, and Counter-Strike. 

The system does not have any of these hangs when booting from recovery and attempting to load those programs.

---

### Post by kc1di on 2018-12-04
The hanging may be a separate issue.  do you know what video chipset is being used?  If it's Nvidia you'll need to add nomodeset to the boot line in grub. 
I still think xubuntu or lubuntu may be better choices for that machine. Good luck.

---

### Post by sufojareth on 2018-12-04
Mobile Intel® 965 Express Chipset Family is the video chipset. I'm completely open to trying other distros as long as they're user friendly and I can install Steam and Discord.
All I'm really using this laptop for is to play some older games via Steam and DOSbox.

---

