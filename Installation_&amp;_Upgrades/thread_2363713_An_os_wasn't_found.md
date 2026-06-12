---
title: "An os wasn't found"
date: 2017-06-13
forum: Installation &amp; Upgrades
---

### Post by ty2525 on 2017-06-13
I bought a dell dimension e510 from some guy last week. I put a new CPU (intel Pentium d 945 3.4GHz) and 4gb of ram along with a geforce 210. I tried to install windows 10 from a usb because the product key didn't work for windows 8.1. Once it got to a certain point the screen turns black and shows there is no single. So I tried to install linux 18, 17, puppy, ubuntu 14, and linux lite. All with the same error an os wasn't found remove devices that don't contain an  os.  I think its a firmware issue right now its running bios revision a05. If there is an distro that will run on A05 I would love to know.

---

### Post by oldfred on 2017-06-13
I do not know Pentiums.
But do you have the PAE issue.
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)
> A number of older [Pentium M]("http://en.wikipedia.org/wiki/List_of_Intel_Pentium_M_microprocessors")  processors produced around 2003-4 (the Banias family) do not display  the PAE flag, and hence a normal installation fails. However, these  processors are in fact able to run the latest (and PAE-demanding)  kernels if only the installation process is modified a little. The  problem is not missing PAE, it's about the processor not displaying its  full capabilities.


---

### Post by ty2525 on 2017-06-13
Alright so by using a dvd it should fix the problem?

---

### Post by oldfred on 2017-06-13
You probably should try Lubuntu, it used to be better with the PAE issue.
But with 4GB & a video card full Ubuntu should run.

With the nVidia card you probably need nomodeset to both boot installer and boot the first time after install or until you install correct nVidia driver. That card may require a legacy nVidia drive. Only install fromUbuntu repository.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

        Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

### Post by ty2525 on 2017-06-15
I burned lubuntu 17.04 to a dvd-r and it worked to boot but it will randomly just stop showing video or it will completely restart. I put the original cpu back in and  it does the same thing so I think its my graphics card. I have linux mint 18.1 on a disk too and I tried it, but it has yet to make it to the desktop without restarting or the graphics going out. I marked nomodeset on the other options by pressing f6 in the lubuntu boot screen, I am not very good with these terms so bare with me, it seems to have changed nothing other than the loading screen and the graphics still stopped just a few seconds into the loading screen. I changed the splash to nomodeset and it went through its things then the graphics cut out again then it restarted and went to its normal "strike the f1 key to continue" and if you do it says no os for obvious reasons.

---

### Post by ty2525 on 2017-06-15
I noticed that online they say the capacitors should be flat and not rusted......well 4 near the cpu power cable are kinda rusted and have a little bump, and a couple near what I think is the intel onboard graphics or just an intel chip I cant tell them apart are a little rusted. Now I didnt want to work for 12 hrs a day for the next 3 years to pay off a new motherboard but if this could be what is causing my problems I dont see a reason not to replace it I mean I replaced everything other than the dvd drive and cpu fan/heatsink so I might as well. I will look at them on amazon I got my first 30 days of prime and I want to use it.

---

### Post by oldfred on 2017-06-15
I had a 7600GT video card.
One night I heard a loud pop, but system kept working so thought maybe from outside.
But next morning system would not work at all.
Later found that capacitors can be an issue on some models. And in looking closely most were open some totally open.
But I ended up replacing not just video card, but motherboard also as it would not work after video card literately blew up.

---

### Post by ty2525 on 2017-06-16
Yeah I knew there was something wrong and once I heard that those capacitors could go bad I knew that's probably the problem. One might not be working all of the way and therefore it can't keep up with the power needed since it's stops working at random times. I really didn't want to replace the motherboard but I already put a couple hundred in it to make it fast so I might as well.  I am going on vacation this week if the new motherboard fixes the problem I will tell you. Thanks for the help.

---

### Post by mörgæs on 2017-06-18
PAE is only a problem for the oldest part of the Pentium M series. As this is a Pentium D we don't have to worry about PAE.

Hardware could be a problem but first I suggest that you try installing using the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"). Post back when you have a working environment with only a command line. 

You just have to read the top part of the text linked to. The bottom part is outdated.

---

### Post by ty2525 on 2017-07-14
My new motherboard is getting here wed. I did research and found that turning off/ restarting at random times is a sign of motherboard failure. The computers stock psu and motherboard are not very good.

---

### Post by efflandt on 2017-07-16
Normally Dell 305 watt PSU's are decent (compared to overrated HP OEM PSU's). I put my 116 watt GTX 550 Ti in an even older Dell Dimension 4700 with old single core Pentium 3.2 GHz hyperthread that does not even do SpeedStep and is 32-bit only. Had to use (2) 4-pin drive to 6-pin power adapter for the graphics card. Its 305 watt PSU had no trouble running 240 watts (measured AC input with "Kill A Watt" meter). However the old Dell 4700 only has PCIe 1.0, so most any graphics card is wasted in it (had to throttle streaming video to 480p to avoid momentary freezes due to dropped frames). My current 7 yr old Dell XPS 8100 is much faster not using that much power (very brief peak to 236 watts) upgraded to i7 870, 16 GB 1333 RAM, GTX 1060 (OEM 350 watt PSU).

That is in contrast to an HP desktop from 2004 where its overrated 250 watt PSU would not even boot 130 watts (off in 3 seconds) after mild graphics card upgrade, measured after upgrading PSU to 330 watt.

---

