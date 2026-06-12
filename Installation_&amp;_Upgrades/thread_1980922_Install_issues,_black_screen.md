---
title: "Install issues, black screen"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by Tyrande on 2012-05-16
I am installing on a freshly built computer. IE blank hard drive (no drivers instealled yet ect). Ubuntu is the only OS.

Motherboard: ASRock Z68 Extreme3 Gen3 LGA 1155
Processor:Intel Core i7-2700K Sandy Bridge 3.5GHz 
Video Card: EVGA 015-P3-1580-AR GeForce GTX 580 (Fermi) 1536MB
Ubuntu Version: 12.04 (64bit)

I want to say...it's been hell installing Ubuntu. I've been at this for 4 hours, and I feel like screaming. I am new to Linux, I have no idea what any of [_this_]("http://ubuntuforums.org/showthread.php?t=1743535") is but it sounnds like what might be going on. I have no idea.

I burned the Ubuntu ISO taken from [here]("http://www.ubuntu.com/download/desktop"). Went to install it and it hung on the welcome screen. I got no option to select language, just a white square on the Ubuntu backdrop. 

I let it sit for a half hour, retried a couple times. Read about pressing shift to access the LiveCD options. On a side note while doing all of this I had severe flickering. Which led me to believe this freezing might be graphical and due to my video drivers not being installed. 

More reading led me to disable nomo something or other on the F6 more options menu. After that Ubuntu began to install. I walked out of the room, and came back to find a blank screen. My monitor was not receiving input. I restarted to a command prompt. Ended up re-installing and deleting the old install.

I stayed in the room through the second install, and it did so with no errors. I said it was going to reboot, screen went black, and my monitor said it wasn't getting any input. More reading led me to type <Ctrl><Alt><F1> which brought up a command menu. 

I have no idea what to do at this point aside from ripping out some hair.

At this point I need to be installing drivers but I have no idea where to go after this. Please help, and make my headache go away.

---

### Post by 2F4U on 2012-05-16
So it seems as if the nomodeset option helped to get the system installed. However, this option is not carried over to the installed system. So, I would suggest that on reboot you attempt to get into the grub menu and then add nomodeset again. The steps are described in the first link of your post.

---

