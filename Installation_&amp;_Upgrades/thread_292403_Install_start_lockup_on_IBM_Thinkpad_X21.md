---
title: "Install start lockup on IBM Thinkpad X21"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by carl spackler on 2006-11-03
Hello,

I bought a IBM Thinkpad off Ebay that supposedly had XP Home loaded, but Micosoft tells me it is illegal and for $150 they’ll  clean up the license.  The Thinkpad has a Windows 2000 license sticker on the underside.  I just want to use the Thinkpad for couch surfing, text, and as a Linux learning tool.
Anyways I was curious about Linux so I bought a Linux Format magazine( $20 ) with a 3 CD ,Ubuntu 6.06.  I live loaded it on my desktop machine fine and easy, and have a dual OS machine now.   However the old Thinkpad is another thing.  It locks up on the install page.

I put the  live cd in an usb cd/rom, reboot and Ubuntu comes up at the ‘flash’ page.  If I wait 30 seconds, it locks  up.  
If I press enter as it highlights the “Start/Install” option, it locks up.
If I press escape and go to the boot prompt and press enter, it locks up.
If I highlight the “Safe Graphics” option, hit enter, it locks up
Highlight “Check CD for defects”, hit enter, it locks up.  (Note;  this is the same CD loaded successfully on my desktop machine. )
Lastly, “Memory Test” , enter.   Works just fine.

I get out of the lockup by shutting down.  Powering up boots me back to the “Start/Install” page just fine.


I have,
IBM Thinkpad X21
Chip Intel i440BX
Memory 256
Pentium III, 700mhz
Hard drive is 20gigs, 85 percent empty.  I disk fragged it.
Running unlicensed Windows XP Home, no other programs.


On the Boot prompts, all I get back from various attempts at cheats are, “ bla,bla…could not find kernel image.”

Thanks.

---

### Post by michaeljking on 2006-11-13
I have had similer problems myself, on and off with my thinkpad T21 and edgy live cd, I had no trouble with 5.10 livecd last year.  I would recommed you download the alternative installation disc and install from that one.

I have just installed xubuntu this week instead of ubuntu, but I will probably reinstall ubuntu as I have been using it for a year now and feel more at home on it.

---

### Post by stelloscuro on 2006-11-14
I had the same problem  with a T21 I bought, the problem is that the installation program loads into ram and I had to get mine up to 384 megs before I could install edgy normally, hope this helps!

---

### Post by freshofftheufo on 2006-11-30
Has anybody had better luck with Thinkpads? Mine is pretty old, A20x I think, and I'm having almost exactly the same problem. The LiveCD worked with Ubuntu to a certain degree, but now the Xubuntu LiveCD does nothing but crash. I can't even get it to detect the Xubuntu alt. CD, and I've reburned each CD multiple times. So lost!

---

### Post by aulax on 2006-12-04
I was getting the same thing, tried installing both Ubuntu 6.10 and Xubuntu. Would hang on the installation screen. after 2 failed installtions where I did a hard reset, I then tried cancelling the installation. When I did that, I got "are you sure you want to cancel or quit" pop-up box. I then selected "cancel" instead of confirming "quit" and the installation actually began.

I had begun to wonder if it was a Ultrabase issue with the X21 since the CD and floppy drive reside in it. Had issues with the IBM BIOS updates.

---

### Post by davbeck on 2006-12-19
OK I have been doing alot of research about ubuntu and ibm and from what I can figure all these problems are with ibm thinkpads. I have tons of a21m thinkpads and have problems with all of them. from audio to downloading updates to not being able to boot the live cd.

what did work though was the cd that they send free. for some reason a workable download cd just doesn't want to work.

I think we should all complain or file a bug report or something.

---

### Post by catalina on 2006-12-20
I was beginning to think I was going crazy.  I installed my live cd on my compaq e500 but couldn't with my t21.  I am leary about trying xubuntu though, it seems like there could be some potential issues doing that as well.  I think I will order the cd and try that rather than boosting the ram.

---

### Post by Titus A Duxass on 2006-12-20
I had no problems with my old T20, I used the alternative CD.  I never use liveCDs, I have tried but they seem to cause more problems than they are worth.

---

### Post by catalina on 2006-12-22
Hey buys and gals, I found out a couple of the hickups with edgy.  Firstly, you have to install the i386 version of edgy, not the default one that it takes you to.  I kept getting locked up with the "download this one if you are not sure" version.  I have 5 t21 thinkpads and a couple compaq e500, all P3.  The Compaq's would take the default download, the thinkpads had to have the i386 version.  The i386 should work with 128 mb ram.  I was browsing through another thread where someone does have edgy on a t21 with 128.

Another thing that keeps hickuping is the wireless network adaper.  I had to go through the repositories and download the 386 file in order to get my d-link dwl 650+ working, which would work off the install with dapper and breezy, but not edgy.

Hope this helps.

Dean.

---

### Post by catalina on 2006-12-22
I left out one more thing.  I don't know if it is because I was playing with ndiswrapper or not, but every once in a while when I try to boot up I get the black screen.  When I pull out my network card I can login no problem.  It might be my fault, or it might be an edgy issue, I am not sure.  I am not a programmer so I don't want to pour blame on anyone because of my lack of understanding.  I just want to give my experience and help out the community.

Dean.

---

### Post by gigaferz on 2006-12-23
same here
ibt t20 
6 gig hdd , 384 ram

while running the livecd it(loading drivers) showed me a message that it could damage my eeprom, iipcxsmbus(?)

im running puppy linux , its running good but i like more any ubuntu version better
last time i tried it i think it damagedmy win 2000 installation

---

### Post by jogege on 2006-12-31
Running Edgy on an IBM X21 without any problems and I am using Ndiswrapper to get my wireless card working.

Installation has been crazy though. Before this I had a 600E and 570 and they both ran any form of Linux I threw at them, Mepis, Suse,Kanotix,Knoppix, they all worked without any issue.

The DVD drive though seems to be the problem I have. It doest recognize some forms of DVDs and really refuses to load any form of Live CD. The drive did the same when I used it in my 570 so I do know its not an issue with the X21.

I have had to use the server instal CD though and I always use the cheatcode "Linux acpi=off pnpbios=off" when am booting off. If I dont do that, it locks up. Once I use that, it installs without any problem and once the server is installed, I use Nana to update the sources list and then do an "apt-get update and apt-get install ubuntu-desktop". Hope this helps.

---

### Post by Iceman404 on 2007-04-19
I am running Edgy on an X21 and a T23 and both of them have been completely flawless after I got them to install. The T23 in particular was easy. I just put in the i386 cd and went from there. For both of these I had to use ndiswrapper for my Linksys PCMCIA card, but after that I haven't had any issues.

I have to admit, installing onto the X21 was a pain. My friend also has a T23, so we installed linux onto my hard drive in his computer, put it back in my X21, and reconfigured the x server. After that it was just configuring ndiswrapper and away I went.

Hope this helps.

---

