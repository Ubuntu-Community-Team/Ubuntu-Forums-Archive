---
title: "nvidia still failing - pre-install script says 'exit'"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by davedaveh on 2010-11-20
I'm in 10.10 installing nvidia 96.43.19 The driver is brand new!
It's been quite a run-around trying to get the Nvidia driver working.  I have already followed a lot of instructions, at least once.  I still get caught at "the pre-install script failed".  When I looked at the script itself, it says it's "triggering an error status to prevent the installer from overwriting ubuntu's nvdia packages."
Some say this script can be ignored, but it seems to be the only thing keeping my install from working.
Some say install from root prompt, some say GUI OK.  Some say d/l from NVIDIA, some from repository.  I have been doing root, init 3, removing old drivers, etc....
This horse is getting really beat up!

Thanks

---

### Post by Hippytaff on 2010-11-20
You tried blacklisting the old driver?

---

### Post by davedaveh on 2010-11-20
I double checked what I did in modprobe and found a typo:

blacklisy nvidiafb

Thanks, but I'll be back after I fix it.  What about that script?

---

### Post by Hippytaff on 2010-11-20
sounds like you have identified the problem, if you still have troubles, post back :-)

---

### Post by davedaveh on 2010-11-20
Fixing typo did not allow the install.
Now I have to go back and change the xorg.conf again so I have some GUI.

Is my "blacklist nvidiafb" correct?  
I don't know why, but someone suggested writing that phrase.

Is there anything else to be blacklisted?

---

### Post by Hippytaff on 2010-11-20
> **davedaveh said:**
> Fixing typo did not allow the install.
Now I have to go back and change the xorg.conf again so I have some GUI.

Is my "blacklist nvidiafb" correct?  
I don't know why, but someone suggested writing that phrase.

Don't know if it is correct...can't see it :-)

anyway, you need to find out the name of the driver you need to blacklist

```

gksudo gedit/etc/modprobe.d/blacklist

```
edit the file with
blacklist "driver_name"
and save :-)

---

### Post by davedaveh on 2010-11-20
Hippytaff,  initially you suggestied blacklisting the old driver.  How do I know what the old driver was/is or what it is called?

Would it have been nouveau?   ;-?

---

### Post by Hippytaff on 2010-11-20
try
```

lsmod | grep -i nvid

```
if you get an output then that is your nvidia driver, if you don't then there is no driver with that name :-)

---

### Post by davedaveh on 2010-11-20
Thanks,
output is:
nvidia       4700667    0
agpgart        32011    2   nvidia,via_agp

So I assume I blacklist this driver, nvidia, and when the new one is installed (hopefully) it might even be called that too, and then what -- it's blacklisted too?
}:-?

---

### Post by davedaveh on 2010-11-20
I'm totally confused.  What is my OLD driver that I am supposed to blacklist?  What does Nvidia have to do with my old driver if I can not install Nvidia?

---

### Post by Hippytaff on 2010-11-20
In thoery, blacklist this driver, and when your new driver is installed (and not blacklisted btw) it will run the device :-)

And you might need to use the windows xp driver with ndiswrapper

---

### Post by davedaveh on 2010-11-20
I'm stuck on this issue and no one has addressed the script issue.
Sorry -- frustrated.

---

### Post by Hippytaff on 2010-11-20
to be honest I've lost track - a bit - so let me catch up on whats going on here

---

### Post by Hippytaff on 2010-11-20
To be honest (TBH) Nividia, ralink, and BCM (broadcom Drivers) are a nightmare in linux :-)

to be clear the Nvidia driver is for a graphics card? or a different device?

---

### Post by davedaveh on 2010-11-20
Yes, we are checking to see if perseverance succeeds in this case.  
It is a video card I am trying to install for an Acer flat screen.  
I told the guy at MicroCenter (a great computer store in my area), who helped me get a Linux-ready wireless card, what trouble I was having with Nvidia card, and he said it was one of the easy ones!  He told me to run the driver install app from a command prompt.
I think that the script issue is important in my case.  How can I find a new script to replace the non-script that is resident in my nvidia folder?

So is there another video card I should be using?  It might be worth the $40 at this point......But we hate to give up.

---

### Post by Hippytaff on 2010-11-21
Have you read this?
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by davedaveh on 2010-11-21
Yes, that was the first thing I tried, then when it didn't work I d/led .run file from Nvidia.  i suppose I have been going back and forth so much, it wouldn't hurt to try it again.
I did find that in my usr/lib/ I had a folder for Nvidia and another one for Nvidia-96.  Problem?
If you can advise me on how to remove all scraps of previous video drivers, that might help.  But what video driver is in use now?  
And why do I have to edit xorg.conf each time I try to install?  Why do I change "nvidia" to "nv".  I am not understanding enough.

---

