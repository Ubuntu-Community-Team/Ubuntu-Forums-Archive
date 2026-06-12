---
title: "Linux on USB External Harddrive - I think I'm getting close"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by Elevator_Hazard on 2008-01-13
So I've got a MyBook 160gig and I wanted to install linux on it. I followed [a nice tutorial](http://pocketseo.com/scripts/43) with little complications (one I had was where the install would hang a 15% but I fixed that). Oh yea this is 7.10 ubuntu by the way. I set up with ubuntu live cd's partitioner 3 partitions, 1 being 3 gigs for swap space, the other had 35gigs ext3 for ubuntu, and the free space (around 120gigs) was used for a fat32 partition. And well, its not booting. I have set my bios to try and boot removable media (usb) before the internal hard disk (which on that computer is also running a linux, I'm familiar with it so I took the harddrive out of it and used that computer to install ubuntu on). I have checked with qtparted after putting my internal back in the computer to see if the ext3 partition was set as active, and yea, it was. So I don't know what I did wrong. There is no chance the boot loader or MBR on the internal was messed up because the internal wasn't there at the time of installing the OS. One thing I'm tempted to try is create another partition on my external simply for GRUB and have that be active, but I don't know which version to use or how to get it to load what OS and such.

Sorry if that's hard to understand, I kind of thought it out as I typed it. I really just need help in getting the OS to load on most any computer (so like the only stuff I'd need to mess with in a computer's bios is that it should check the removable media for an OS before it checks the internal harddrive(s))

I'm decently familiar with ubuntu (and love it) and also with windows (using it on a nicer computer right now) and also I know some programming languages a little if that helps me at all.

---

### Post by logos34 on 2008-01-13
> And well, its not booting.

The grub menu on the external drive isn't appearing and it just boots to the internal drive, or it is but won't boot ubuntu kernel? 
> 
I have set my bios to try and boot removable media (usb) before the internal hard disk

so it says 'removable media (usb)', or just 'removable media'? i.e. are you sure it supports usb boot?

---

### Post by Zimmer on 2008-01-13
[http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/)

Will this site be of use to you ? I have successfully used Tutorials from there to get Linux booting from a USB stick...

There may be something in the tutorial that will point you to the solution for your particular problem...

Regards

---

### Post by Elevator_Hazard on 2008-01-13
It was Removable Media and no, I'm not positive that computer's bios supports loading off of a usb. Its version is 4S4eb2x0.86a.0023.p16 and I had no luck finding anything useful on it... And there is no grub menu, or well... Grub 1.5 appears in simple text at the startup but then it just continues to load the other linux OS I have on it... And before I never noticed or saw Grub 1.5 show up when it did.

---

### Post by Elevator_Hazard on 2008-01-13
> **Zimmer said:**
> [http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/)

Will this site be of use to you ? I have successfully used Tutorials from there to get Linux booting from a USB stick...

There may be something in the tutorial that will point you to the solution for your particular problem...

Regards
Sorry I just noticed that post. I actually tried and did most everything there except I did a manual partition at that step.

I ended up having it like so:
3000mb swap (couldn't select mount point as expected)
35000mb ext3 (I installed ubuntu here, mount point was /)
113.66gb fat32 (this is going to be used for sharing stuff between windows and linux on the other computers where I have and use windows, mount point was and had to be /windows)

---

### Post by logos34 on 2008-01-13
> **Elevator_Hazard said:**
> It was Removable Media and no, I'm not positive that computer's bios supports loading off of a usb. Its version is 4S4eb2x0.86a.0023.p16 and I had no luck finding anything useful on it... And there is no grub menu, or well... Grub 1.5 appears in simple text at the startup but then it just continues to load the other linux OS I have on it... And before I never noticed or saw Grub 1.5 show up when it did.

You need to consult the Bios section of your computer's manual to verify if it can boot usb.  

If not, you have a couple of options: if your other linux on the internal also uses Grub bootloader, then you could try adding an ubuntu entry--it might be able to boot the usb.  

Or add a separate grub /boot partition on the internal. ('[booting kernel from internal hard drive]("https://help.ubuntu.com/community/BootFromUSB")')

---

### Post by Elevator_Hazard on 2008-01-13
I don't have a /boot partition on my external... Could I put it there? What goes in there/where is it available for me to get and what format? I think this would be better as I plan on using this on a few computers.

As for the computer manual, I have none. The computer is 11 years old I think and I got it in a class I took.

---

### Post by logos34 on 2008-01-13
If it's that old chances are it does not support usb boot.  So you'll have to be creative.

Actually you do have a /boot directory on your external usb, it's where the kernel images and grub files are stored.  All you'd be doing is copying the files from it to another separate /boot partition on the internal drive.  The problem is the machine/bios cannot 'see' the usb drive at boot.  So you'd boot up and select the kernels on the internal drive, they would run but would be using the root partition on the usb.  You can still plug the the usb into any other machine that supports usb boot and run ubuntu.

But you might want to first try simply adding an ubuntu entry to your existing linux bootloader on the internal.  You may be able to start ubuntu that way.

---

### Post by Elevator_Hazard on 2008-01-13
That was the problem... I tried it on this computer and it worked (that's why I took so long)

Only problem is it started up saying it couldn't find my video settings so it used safe graphics mode and I couldn't get it higher than 800x600, probably an easy fix, I'll look it up later unless someone knows how to fix it off the top of their head.

---

### Post by logos34 on 2008-01-13
> **Elevator_Hazard said:**
> That was the problem... I tried it on this computer and it worked (that's why I took so long)

What worked for you?

---

### Post by Elevator_Hazard on 2008-01-13
> **logos34 said:**
> What worked for you?

Sorry, ubuntu did on this computer (the good newer one).

---

### Post by Zimmer on 2008-01-14
> **Elevator_Hazard said:**
> That was the problem... I tried it on this computer and it worked (that's why I took so long)

Only problem is it started up saying it couldn't find my video settings so it used safe graphics mode and I couldn't get it higher than 800x600, probably an easy fix, I'll look it up later unless someone knows how to fix it off the top of their head.

I imagine you can solve this by copying the settings from your other xorg.conf file (the one on the internal drive) to the xorg.conf on the External drive..(backup first, of course).

---

### Post by Elevator_Hazard on 2008-01-14
Hmm... Xorg.conf? I tried to configure myself but I couldn't get it right... Also this monitor and graphics card is different than the older computer I used to install ubuntu on my external (I did that because I'm more familiar with that old computer's insides and it was just sitting there for me to use whereas this computer is harder to get out of shelf).

So maybe I should get the ATI drivers I know of (if they are available for linux) but I don't know about the monitor problem (couldn't find what it was except plug`n`play which it might be...). Its annoying using 800x600 when it should be 1280x1024 :D

---

