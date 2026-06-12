---
title: "Unable to install/boot with 7600GS PCI-e card"
date: 2006-05-26
forum: Installation &amp; Upgrades
---

### Post by yamaz on 2006-05-26
Okay, kinda new at this, bear with me....

Have tried five different distros of linux, all with the same result.  No installer, for any of them, wants to work with my Nvidia PCI-e card.  Invariably they all freeze when they start polling for video cards or changing screens.

If I use the onboard video, installation for Ubuntu goes off without a hitch, everything works right off.  So I thought I would be smart, got it installed, downloaded Nvidia drivers and installed them.  (Must have done it right, because now X won't work with my onboard lol).  Anyway, rebooted, plugged in the 7600 and sure enough Ubuntu froze at exactly the same point as before. (Right after starting hotplug.....but I know that it's the video from other installs).

I know other users have PCI-e cards.  I don't understand why I'm having such an issue with it.  One thing I do find odd is that the Intel mainboard doesn't have a bios setting to disable the onboard, only to boot the slot first.  Does that seem strange to anyone else?

Anyway.....here are my specs...

Pentium D930 dual-core 3.0GHz
Intel D945Gnt mainboard
BFG Nvidia 7600GS 256M PCI-e (obviously)
1Gig Apacer dual-channel DDR2 (don't know the timings offhand)

I don't know what else to do.  I only know enough Linux from my Unix days at high school.  It has been over a week now, and I am about ready to throw in the towel.

If anyone has ever encountered this, or knows of an argument I'm missing, please let me know.

EDIT:  Almost forgot.....I have tried noapic, nolapic, acpi=off, pci=noacpi and all combinations of them.  Might it have something to do with the agpgart?

---

### Post by CyberCam on 2006-08-22
](*,)

---

### Post by djRobbieF on 2006-09-02
I also just bought an nVidia 7600GS, but mine is AGP and I am having a similar problem; I cannot even boot from the Ubuntu live disc.

Is this chipset not yet supported, or what?

Any help would be appreciated - I actually bought this card thinking i'd be able to switch to Ubuntu (I'm a Linspire user at present).  I wanted the nVidia chipset so I could install XGL and have it run relatively well under Ubuntu; but now that I've installed this card, I cannot even get IN to Ubuntu.

Thanks!!

---

### Post by nin82 on 2006-09-05
m8s the best thing to do rigth now since no one actualy replys to this is (if its already installed)do "dpkg-reconfigure xserver-xorg" and use the VESA drivers instead of the Nvidia one then press enter to anything that u dont know the answer to or just follow the recomendations. thats what i did and thats what worked although still no 3d acceleration nor real nvidia 7600gs drivers running!  but the 2d is fair enough!!! if not installed then use any old card i guess good luck!

---

### Post by CyberCam on 2006-09-06
Good News! The new 8774 drives worked with envy! I'm now up and running with 3D acceleration.:-D

---

### Post by nin82 on 2006-09-06
same here this is what i used: 
[http://www.ubuntuforums.org/showthread.php?t=52924](http://www.ubuntuforums.org/showthread.php?t=52924)

---

