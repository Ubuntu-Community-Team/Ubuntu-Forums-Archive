---
title: "Install dies on Dell Dimension 8300 w/ ATI Radeon"
date: 2006-08-20
forum: Installation &amp; Upgrades
---

### Post by sadalmelik57 on 2006-08-20
I want to dump windows, but I can't get Ubuntu 5.10 to install on my Dell Dimension 8300 with ATI Radeon 9800 Pro with 128mb (1028mb Ram, P4 3.06gh).  During the install the video stops functioning.  I can hear audio music play but the 15" SVA LCD monitor has a message that says it is not receiving a signal, and it goes to sleep.  If I briefly touch the power button the video wakes up, but the installation stops.  I've tried using "boot:Live aic7xxx=no_probe vga=771" and both of them seperately with no luck, and I started it in live-expert mode to see if any particular option was causing the problem.  The error occurs after I see the brown Ubuntu screen checking different installations with "OK" on the right side begins and usually dies just after "Starting Bluetooth Service . . . OK.  HCID SDPD"  I have no network, bluetooth, or similar service just good old dial-up.

Which brings me to my second question, which is Where the heck is the dialer program in Ubuntu?  I can't get online and I can't find a modem on any computer I've tried the Live CD on.  Don't tell me I have to download it!  Will it be included in the Installed version?

---

### Post by em3raldxiii on 2006-08-21
I see no one has answered you yet, so I'll bump you up the list a little.  The only solution I can think off off-hand is for you to download Ubuntu 6.06.1 and try it instead.  The biggest change between versions is a VAST increase in native hardware support.
 
As far dial-up is concern ... uh ... I have no idea.  I haven't had to deal with dialup in so long now that I would be in the same boat as you ;)  Good luck!

---

### Post by sadalmelik57 on 2006-08-23
Thanks very much for your assistance.  My copy of the Dapper release is 4 - 10 weeks away, and with dial-up it is unreasonable to download.  I've got a copy of Freespire, but like Breezy Badger there is some problem with the video, at least on the first attempt to run it from the live version on the CD.  I hope that Dapper Drake will resolve that since it happens in the installation and I have no way to correct it.  

After reading other resources over the last couple days I can see that there is no easy answer to the question about a dialer and using a modem.  I'll wait (impatiently) for my Dapper Drake CD's to arrive and hopefully get a clean install and then start messing with the modem.  Sounds like fun.  I miss DOS.

---

### Post by em3raldxiii on 2006-08-24
That is definitely the largest drawback for Ubuntu - dialup.  Once you are fully up-to-date, most updates thereafter will be small (under 5 MB) so won't be terribly painful on dialup.  But from the base install to the updated (or modified) version might require some patience.  If I was in your position, I would grab my computer and go somewhere with highspeed (friend, school, library) and do the install/upgrade/modification there to avoid going insane.
 
There are other distributions that offer multiple CDs to prevent a user from having this problem - and maybe Ubuntu will offer a CD snapshot of some of their repositories at some point.  If you want to try another distribution that reaps many of the same benefits of Ubuntu, try Mepis.  I noticed that another user here (ayisu) promotes mepis as an alternative for some people, and I am going to try it for one of my extra computers.  You can get 3 extra CD images that include a vast array of additional software.
 
Keep us updated!

---

### Post by sadalmelik57 on 2006-08-24
I was able to boot my P2 400mhz 320mb with the live-expert method just by entering through all the pre-chosen options (without Expert it would hang on the keyboard settings).  It also boots to Freespire with no problems, but both Breezy Badger and Freespire have problems with my newer more powerful Dell.  Go figure.  I suspect it is in the ATI video card.

I have a friend with high-speed who says he will download Dapper Drake for me, so maybe I can give it another shot next week.

---

### Post by em3raldxiii on 2006-08-25
Yup, dapper's biggest benefits are that it supports a vastly larger array of hardware - including, I believe, some ATI devices.  As far as I know, Ubuntu (and linux in generall I think) has always had a hard time with ATI devices because of extraordinarily poor driver software permission/copyright.  If these darned companies would just make all their driver code open to the public we wouldn't have any of these problems.

Anyway, yes ... I am eager to find out how Dapper handles your new computer.  And who knows, perhaps what you discover can help developers come up with an even better Ubuntu for the next release.

---

### Post by sadalmelik57 on 2006-09-10
I finally got a good copy of Ubuntu 6.06.  Like the 5.10 version, it died when installing the Live CD, however I used the second option, safe video mode, and it worked fine.  I think that supports my notion that the ATI Radeon video card is the demon.  

I'm off to explore Ubuntu and make room on my hard drive for a dual boot.  Thanks for your help.

---

