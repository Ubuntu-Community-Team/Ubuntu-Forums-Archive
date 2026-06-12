---
title: "8800GTS ubuntu 8.04 can't do GUI install.."
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by superuzr001 on 2008-05-30
Ok I have a problem.. don't we all.

I am trying to install ubuntu v8.04 and when I select "install ubuntu" using the graphical interface, the ubuntu screen attempts to come on then I get the command prompt.  I tried this multiple times and it fails to load the graphical install.

My system is:

Core2Duo 2.4
4GB Ram
8800GTS PCE express
Dell 21" LCD monitor

I tried to do this on my other system and it worked fine for the graphical interface no problem.

Pentium 2.8
1GB Ram
7800GT agp
Compaq 21" CRT monitor

I am kind of bummed out cause I have been using ubuntu for a while and I really like it but if I can't get a fix soon I think I'll have to DL another distro.  I don't know if this is a common issue with this release and I am somewhat casual with the whole linux thing but I'd like to get some feedback before I go with anything else.

Thanks in advance,

ML

---

### Post by tamoneya on 2008-05-30
use the safe graphics mode.  I think they moved it into the boot options on hardy.  On gusty it used to be one of the main options.

---

### Post by superuzr001 on 2008-05-30
that is the option I used for the install (the only gui one i belive)

---

### Post by Gripp on 2008-05-30
I have the 8800GTX and ubuntu installed okay.  maybe try burning a new CD and booting from it rather running it in windows first...

if you cant do the install at least see if you can get into a Live environment.

---

### Post by superuzr001 on 2008-05-30
I cannot get it into the "live environment option" takes me to the same place as the "safe graphical option" which is the console.

I really appreciate the fast replies ty.

---

### Post by superuzr001 on 2008-05-30
I got the disk from OSdisk delivered today both dvd and cd verions and no go :/ just thought I throw it in there.

---

### Post by superuzr001 on 2008-05-31
I am pretty sure that the video card is the issue.  My monitor supports standard resolutions as well as wide screen, however I don't have another PCI card to throw in there atm hence no way to test my theorycraft.

---

### Post by superuzr001 on 2008-05-31
*bump*

---

### Post by Gripp on 2008-05-31
there isn't really a "live" option

it is just something like "try ubuntu with no change to my system"
or close to that at least...

are trying to start the CD from windows and selecting the install option there? or are you booting directly to the CD and using that install menu?

and you say that once you try to install it you get dumped to a console.  is it a working console?

try "startx" and let us know what the outcome is.  any errors or whatever, post em here. 

and i'm heading to bed here - so hopefully you get the help you need.  good luck!

---

### Post by superuzr001 on 2008-05-31
I refered to live option because it's a live cd after all but you are correct the entry is called something along your lines.  I had a previous version of ubuntu on my system, no windows installation on any of the partitions and I boot straight from the cd and when I get the command prompt.  The command prompt is usable but I do not have any idea how to build this os from scratch.  Startx does not work, it tells me that its not found.  I'll be checking the boards this morning see if anyone can give me some ideas.  Thanks again.

---

### Post by superuzr001 on 2008-05-31
Any ideas anyone?  I really need to get an os up and running today, so unless someone got some good pointers I will have to load Fedora 9.

---

### Post by CameO73 on 2008-05-31
It's weird ... I had no problems installing Ubuntu 8.04 with my 8800GT. Anyway, you could try the alternate desktop CD (see [here](http://www.ubuntu.com/getubuntu/download); the trick is to check the 'Check here if you need the alternate desktop CD ...' option just below the Start Download). That is a (pretty simple) text installer that should not fail.

Look [here](https://help.ubuntu.com/community/Installation) for some more info on the alternate installation.

---

### Post by superuzr001 on 2008-06-01
I ended up diggng in the closet for an hour for the v7.04 installation disk then did the upgrade to v7.10 and doing the upgrade to v8.04 now.  Although, it isn't a fix to my problem it is a way around it.  Thanks for all the feedback.

---

### Post by CameO73 on 2008-06-01
Wait ... you could install 7.04 with an 8800GTS installed? I remember (and have experienced) problems with the 8xxx series and 7.04/7.10 installations. In fact, 8.04 is the first Ubuntu release that I could install from the LiveCD with my 8800GT, since it includes a pretty new nVidia driver. With the other ones I had to do some annoying stuff (like disabling the restricted driver management, getting the latest driver from nVidia, and spending some time in the xorg.conf).

Anyway, good to see you found a solution!

---

### Post by superuzr001 on 2008-06-01
Yes, installed 7.04 no prob.  The transition to 7.10 and from 7.10-8.04 was hella long. I got everything up and running. World of Warcraft runs really smooth.  I am having an issue with nvidia on my other rig so I put up a post on the video boards.  Other than that everything is running smooth, thanks.

---

### Post by Riivoz on 2008-06-10
Hello, this is my first post here, i guess and, I'm really sorry if it's an old topic or something [I'm too lazy to check it], but I have the same error on my pc when I try to install ubuntu 8.04. It like, goes into console, where it keeps "writing" all kind of stuff :\ which I don't understand at all. My "dinosaur" machine is:
1GH/z amd athlon
256mb nvidia fx 5500
318 SD-ram 

So, any ideas how could I fix it? x.x

---

