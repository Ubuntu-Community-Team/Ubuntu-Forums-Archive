---
title: "Installation Failure"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by Platinum89 on 2006-09-07
I'm attempting to change my friends system over to Ubuntu, however I'm encountering serious failures. Below are some specs first.

System Specs
Previous o/s : Redhat 9

Pentium 366Mhz
Memory 192MB
hda : 10Gb
hdb : 4gb
(not sure what else you'll need)

During the installation, it gets past installing OpenOffice and then I get the red screen stating setup failure. A failure to install software , although it doesn't tell me what. I tried three times and each time it does the same thing. I've tried the Alternative CD as well. I have verified there is nothing wrong with the system itself. It is an older system so I burned the cd at 24x, which it reads without any problem (When I installed Redhat, it was from cd's burned at 48x).

Any help would be appreciated. I need to get his box online by the weekend.

---

### Post by zxee on 2006-09-07
Check out the hardware support section [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
that computer might be a little old/underpowered for 6.06 with gnome or kde.
You might do better with xubuntu on an older guy like that.

---

### Post by Platinum89 on 2006-09-07
I downloaded it an burned to a cd. I'll give it a go today. If it fails, I may end up having to resort to that horrible o/s that I won't mention. I'd rather not as you can probably understand ;)

Thanks for the help :)

---

### Post by wpshooter on 2006-09-07
You probably need to see if you can burn the Alternate ISO image at 4X if possible.

And then make sure you run the "check CD integrity function" on the initial Ubuntu boot menu.

And if it passed the integrity test, then install in TEXT mode.

Good luck.

---

### Post by zxee on 2006-09-07
> **wpshooter said:**
> You probably need to see if you can burn the Alternate ISO image at 4X if possible.

And then make sure you run the "check CD integrity function" on the initial Ubuntu boot menu.

And if it passed the integrity test, then install in TEXT mode.

Good luck.

We're talking about using xubuntu here because of the computer's age/speed.
[https://help.ubuntu.com/xubuntu/desktopguide/C/introduction-chap.html#about-xubuntu](https://help.ubuntu.com/xubuntu/desktopguide/C/introduction-chap.html#about-xubuntu)
I don't think there is an alternate cd for xubuntu.

---

### Post by Platinum89 on 2006-09-08
I finally was able to get the installation completed. Bit of work involved in it, but at least it worked. Just in case others are experiencing something similiar, I'll explain what I did to reach success. First, Ubuntu is the only o/s on the box. It's not a dualboot setup. I started off by downloading 5.10 Installation (not the LiveCD) iso and burned the cd. Dropped that in and followed the prompts. Installation was completed. Then the notice of update popped up. Followed the instructions. One item didn't get updated, something about the server reset or something. Anyway, I let it try again for that specific item, which it obtained and applied. The system is now running 6.06 without a problem.

Now, I do have a question though. Everything was detected but the sound card. Nothing special, just your average 16 bit Sound Blaster. Any suggestions how I can Ubuntu to see it?

Thanks for all your help folks. Great community here.

---

### Post by Platinum89 on 2006-09-08
Disregard. Seems it can't see any 16 bit card, including the modem. I took the 16 bit SoundBlaster out and popped in a PCI soundcard. It detected it without a problem and all is well. Took the box back over to my friends place and the he is a happy camper. Likes the interface too and everything works! 8) ;) 

Thanks all!

---

