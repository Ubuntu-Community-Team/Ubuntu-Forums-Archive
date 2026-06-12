---
title: "Can't run Ubuntu from the Live CD"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by BlkMagik07 on 2007-02-26
Hey everyone.  I'm a current Windows user that wants to make the permanent move over to Linux and was told that Ubuntu is a great Linux distribution to start with, so I decided to download it.  I burned the iso properly but for some reason when it tries to boot Linux from the CD I get a blue error screen saying something about an X server graphical interface being unable to run.  I don't know why this happens but it's weird because it works on my secondary (mom's) PC just fine.  Can someone help me out because I really wanna get Ubuntu up and running before I go to sleep tonight.  Thanx =).

---

### Post by Kateikyoushi on 2007-02-26
Try the safe video mode, run the disc error check, if still won't work tell us about your hardware and you could also try the alternate install cd.

---

### Post by BlkMagik07 on 2007-02-26
Tried safe video mode and got the same error.  There is no problem with the disk as it ran fine on another PC but ran the disk check just in case and it also says the disk is fine.  My hardware is as follows:

Dell Dimension e510
1 Gig RAM
Intel Pentium 4 Processor with HT
ATI Radeon x600 HyperMemory 512 MB

---

### Post by Kateikyoushi on 2007-02-26
Well it stops because of your ATI card, you could try to follow the steps he recommends [here]("http://www.linuxmint.com/forum/viewtopic.php?t=1278"), or could use the alternate install CD, I would recommend the second option

---

### Post by BlkMagik07 on 2007-02-26
Well a little update here.  After some extensive research I finally got the Live CD to run.  I used some of the methods in the link you provided such as deleting the splash screen and using the prompt but what I did was this:

Typed startx without changing the xorg.config file.
It brought up the same error but after bypassing those it took me back to another prompt
Typed in '$ sudo dpkg-reconfigure xserver-xorg' which brought up the xorg configuration program
Changed the driver to vesa (as stated in the link you proviided) and at the end of it all, typed startx again and Voila, typing this message to you from Linux and loving it.  I am still debating on whether or not I should permanently install Linux, though. =)

---

### Post by Kateikyoushi on 2007-02-26
That certainly surprised me you could do it so fast and it worked.
You have nothing to loose except a little time if you have a windows CD you can restore your OS the way it was in case you are not statisfied with ubuntu.

If you decide to install I recommend this guide. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

### Post by slayerboy on 2007-02-26
If you do decide to install it, you're going to want to install the ATI video drivers.  BUT, your machine sounds fairly new, so you may have some problems with hardware recognition.  I would definitely check out [http://ubuntuguide.org](http://ubuntuguide.org) for info first.

---

### Post by BlkMagik07 on 2007-02-26
Thank you guys for all your help. ^.^

---

