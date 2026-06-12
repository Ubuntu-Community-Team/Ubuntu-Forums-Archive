---
title: "help installing fiesty fawn on Toshiba X205-S7483"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by webbhawk on 2007-10-06
When I insert the Live CD (from canonical, not a burned ISO)--(tested also) I get the boot screen but when I choose to run the live cd, I get this message:

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

I'm still pretty new to linux. I've been using ubuntu on my desktop for about 4 months now. I'd like to have the stability of ubuntu on my new laptop too. 

Any help?

specs:
Toshiba X205-S7483
Intel® Core™2 Duo processor T5450
2GB DDR2 SDRAM
240GB hard drive capacity SATA 2 drives 140GB each
NVIDIA GeForce 8700M GT graphics

Any more info needed, I will gladly supply.

---

### Post by webbhawk on 2007-10-06
I found the fix on a different site. At the boot menu, hit F6 and add this to the end: all_generic_ide


Now the cd loads but Xserver won't. I've seen this in the forum somewhere before but I can't seem to find the solution. The error screen says No display devices found. I know I have a pretty new graphics card in my laptop.(see above post) 

Any takers?

---

### Post by webbhawk on 2007-10-15
Is there anyone out there who can help with this? Vista is driving me nuts!:confused:

---

### Post by nimitch on 2007-10-18
hi i have a similar computer.. the uk version x200-20s and managed to install gutsy without any troubles .. or I found this thread with some details and a solution but i think its redundant now

[http://ubuntuforums.org/showthread.php?t=519229](http://ubuntuforums.org/showthread.php?t=519229)

also note that there are some sound driver issues ..internal  subwoofer doesnt work and neither does the headphone out jack :-(

i think this is related

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by webbhawk on 2007-10-20
Thanks for the reply but I just found a very easy fix for this problem. INSTALL GUTSY GIBBON!

If there is anyone out there with the same (or similar) laptop that I have, gutsy is the answer. I used the live cd and had linux on my system in 20 minutes with no installation problems. 

Now on to the next issue....(I'll start another thread)

THANKS!

---

### Post by nimitch on 2007-10-21
hi there.. i didn't make myself clear there :-)  the sound driver issues I described above are experienced in a gutsy install .. not feisty.. i would be interested to know if you have the same problems with the subwoofer etc ? 
also I have  a very low volume level compared to the hardware running vista.. 

ps these machines are awesome but I think the lid is  an hugly..

---

### Post by webbhawk on 2007-10-21
Yeah, I have the same issue with the sound. It's something I'll work on later. since most laptops don't have subwoofers anyway, I think it's going to be difficult to get support on this. I also noticed the lower sound.

Graphics were a bit of a pain to get going.(The "new" nvidia drivers I'm talking about)

I'm still waiting on a reply for my bluetooth problem. I had issues with the bluetooth in Vista too so I somewhat expected it in ubuntu.

So far I love gutsy. Just coming from windows it's very strange seeing an OS actually get better with a new version.

p.s.s
I disagree about the cover. I love it. It's what first caught my eye about the laptop. But if you really don't like it. Go to bestbuy's website. they have customized vinyl (i think) covers that look pretty sweet. If I didn't like my cover already, I would have definetly got one of those. Here's the link: [http://www.bestbuy.com/site/olspage.jsp?id=abcat0515025&type=category](http://www.bestbuy.com/site/olspage.jsp?id=abcat0515025&type=category) Click under "Choose you skin"

---

