---
title: "Xubuntu Text-Install Problem"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by metafour on 2007-02-24
Hey guys, so I'm trying to install Xubuntu 6.10 Edgy on my PC using the Alternate CD (Text Install).  I got the CD booting fine and everything is working, but my installation gets stuck when it gets to the Network Configuration part.  It keeps telling me that it cant auto-configure my DCHP stuff, which is confusing me.  I tried doing the manual configuration but theres way too much stuff to fill out which I'm simply not sure about (host IPs and the like), and I dont want to make guesses and end up making a huge mistake.  I guess my question would be: is there anything I can do to get the auto-configuration to work, or should I just choose to continue the installation without setting up the Network?

---

### Post by yabbadabbadont on 2007-02-24
Try doing a cold boot with the cd in the drive.  I get the same problem with most live cd's.  My network card just doesn't get reset properly by them.  I found that shutting down to poweroff and then powering back up gets it to work correctly.  (Hitting the reset button does too, but you have to time it right)

---

### Post by nyinge on 2007-02-24
It could have been a problem with the router not being able to give out an IP fast enough.  (The Ubuntu installer has little patience in waiting for an IP from the DHCP server.)  I sometimes got away with that by repeating the process, i.e. keep asking for an IP even when it fails.  Try it for like 10 times.  You might get lucky.

Otherwise, take the manual route.
- Hostname:  Anything
- Host IP:  An available address on the same subnet on your network.

---

### Post by metafour on 2007-02-24
Thanks guy, I'll try that out and post back.

---

### Post by Herman on 2007-02-24
> or should I just choose to continue the installation without setting up the Network? Hello metafour, 
While I have no doubt that the above posters are correct, it won't matter a hoot if you just choose to continue the installation without the network. 
You can just as easily set up your network connections after the installation is done. For mine at least, it's just a matter of clicking 'System'-->'Administration'-->'Networking', typing your password, choosing a connection, click 'properties and enabling it. (By placing a check mark in the box for 'enable this connection'.  That's for Ubuntu, my PC with Xubuntu in it is busy at the moment so I can't check exactly how you do it in Xubuntu, but it will be just as easy.
I just have a standard wired connection, so I never have any networking trouble. A few who have fancy wireless connections used to have some problems, but I think even most of those are easy to set up in Ubuntu nowadays.

Regards, Herman :)

---

### Post by metafour on 2007-02-24
So it wouldn't be a problem if I just skipped that part of the installation?  I tried again and its still not auto-configuring.  I dont really mind manually doing it but it asks for Netmask, Gateway, Name Server Addresses and the like which I really dont know off the top of my head and dont really know where to find either.  Herman's method seems to be extremely simple, if I skip it it in the installation process will it be that easy to setup or will I still need to provide Netmasks, Gateways, etc. ?

---

### Post by Herman on 2007-02-24
Hmmm, I must make it a point to find out what those networking terms actually mean. I have tried and normally the explanation for those usually involves looking up more networking terms to try to understand what the explanation meant and so on and on...:) he-he!

Certainly I have gotten away without needing to know those since around the last couple of months of the first Ubuntu release, Warty Warthog, and it hasn't stopped me from enjoying Ubuntu.

Don't worry so much.

Whenever I perform an installation and it is connected to the internet I do see the light blinking on my network switch, especially during the 'downloading and installing software' phase. However, unless you are extremely clever and well informed, it's really impossible to tell the difference between an installation that has been performed with an internet connection from one without. Certainly after the first web update I would imagine there would be no difference at all.

But that's just my uninformed opinion. I would be as interested as you to hear from more opinions on this subject.  

Regards, Herman :)

---

### Post by metafour on 2007-02-24
My main problem is that I'm doing a clean install of Xubuntu - no dual-boot partition, so if I screw up this network thing I wont be able to switch back into Windows, get on the internet, and figure out what to do.

Just to make it 100% clear, the problem I'm getting is after this part:

[img]http://doownek.org/fichiers_blade/2_ConfigureNetworkDHCP.png[/img]

The bar fills to 100% and I get this screen:

[img]http://doownek.org/fichiers_blade/3_ConfigureNetwork.png[/img]

---

### Post by nyinge on 2007-02-24
I understand about your worries.  Do you have another box with working windows or linux?

---

### Post by metafour on 2007-02-24
No, this is the only PC I have here (at my house, I go to school in a diff city and I've got a newer PC there).  This PC is in dire need of a fresh start which is why I'm doing a clean install, going to try out Xubuntu because frankly this PC is an old POS which needs a less demanding OS.

---

### Post by yabbadabbadont on 2007-02-24
I would suggest that you download a livecd based distribution like knoppix so that you can at least boot it and have network access.  Of course, you should boot the knoppix cd and verify that your network connection works first.  :)

Edit: I reread your post and saw that you have an older pc.  In that case I would suggest that the livecd you get be wolvix.  [http://www.wolvix.org/](http://www.wolvix.org/)

---

### Post by metafour on 2007-02-25
To add, my ISP is Bell Sympatico and I've got ADSL.  I connect via PPPoE which is likely why the auto-config cant recognize DHCP - because I'm not using it.  If I'm right in my assumptions then that would mean setting up the DCHP stuff would be pointless, correct?  I'm thinking that Herman's original suggestion of just skipping that part and configuring after installation would be the right move, or am I wrong?  

Would running: sudo pppoeconf 

in the terminal solve my problems?  My understanding is that pppoeconf is used to configure a PPPoE connection, which is what I should be doing.

---

### Post by metafour on 2007-02-25
Bump.

---

### Post by metafour on 2007-02-25
Bump again - really need an answer regarding the PPPoE/DHCP stuff.

---

### Post by confused57 on 2007-02-25
Maybe this will help:
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by nyinge on 2007-02-25
Just like other people on this thread said, boot up Xubuntu Live CD, and try to configure your internet using confused57's link.  See if that works.  If it does, then it's very likely that the installed version would work also.

If the Live CD works, yes, skip the internet setup page while installing to your hardrive.  

However, I cannot gaurantee everything will go smooth, as I've never tried PPPoE setup.

---

### Post by popformula on 2007-11-03
The pppoeconf thing is great but it took me ages to find it, and I knew what I was looking for. For less experienced people it could be a real stumbling block. If it could be included in the alternate CD network setup process, things would be a lot easier.

Is this even the right place to make this kind of suggestion?

---

### Post by popformula on 2007-11-03
The pppoeconf thing is great but it took me ages to find it, and I knew what I was looking for. For less experienced people it could be a real stumbling block. If it could be included in the alternate CD network setup process, things would be a lot easier.

Is this even the right place to make this kind of suggestion?

---

