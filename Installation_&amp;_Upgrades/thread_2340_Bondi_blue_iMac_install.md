---
title: "Bondi blue iMac install"
date: 2004-10-27
forum: Installation &amp; Upgrades
---

### Post by cerulean coil on 2004-10-27
I've been interested in using Linux for a long time now, and when I found ubuntu, I'd found the perfect ditro. (For me anyway, I'm not here to start any arguments.) ;-) 

Thing is, I've downloaded the ISO, burnt it to CD-R, and it simply won't install. First off, it doesn't detect any network hardware... which is odd, it has ethernet. "Fair enough" I think, "I can always sort this later."

After that, it does the entire installation, and then tells me that certain packages haven't installed. Basically, all the important ones, including the base debian system, and GNOME. It then opens a screen where I tell it to try and reload the missing packages, which it promptly ignores.

Moving on from that (the only thing I can do) the most I can do is log into a pure terminal session.

Please help!I searched the forum before I registered, and found other people were having similar troubles with iMac, but couldn't really follow the solutions. (Remember, I'm new to all this ;-)). Would a better brand of CD-R help? I'm using 700MB discs that are usually used for music.

Many thanks for any help in advance.  :D

---

### Post by im_ka on 2004-10-27
if you have installation problems, the first thing to do is to check the md5sum of the iso and see if the download is corrupted.

make sure you burn it on low speed (4-8x), so the chance of a burning error gets lower (=0, probably).

also, it's a wise thing to use cd-rw's for burning iso's.

hope this helps. check back if you're still having problems.

---

### Post by FLeiXiuS on 2004-10-27
I'm currently working on installing ubuntu to a iMac, I will let you know how it goes.  

My campus setup:
Dell OptiPlex Something, Dual 17" Trinitron Monitors
Then I have a iMac, which I want to install Ubuntu on.

For those of you who know me, I sacraficed the 3rd monitor for a iMac :-(

---

### Post by cerulean coil on 2004-10-27
[QUOTE=FLeiXiuS]I'm currently working on installing ubuntu to a iMac, I will let you know how it goes.  

My campus setup:
Dell OptiPlex Something, Dual 17" Trinitron Monitors
Then I have a iMac, which I want to install Ubuntu on.

For those of you who know me, I sacraficed the 3rd monitor for a iMac :-([/QUOTE]

But on the other hand, you have an iMac. So it's not all bad. ;-)

Thanks for the info guys.

---

### Post by cerulean coil on 2004-10-27
[QUOTE=im_ka]if you have installation problems, the first thing to do is to check the md5sum of the iso and see if the download is corrupted.[/quote]

How do I do this? I'm downloading via my iBook, and I when I burn the iso I do check the box that says "Verify Burn". Is that the same?

Man, I'm a total newbie.  8-[

---

### Post by Mighty Mik on 2004-10-27
On the PC side, i've found that for whatever reason, Ubuntu likes to be burned as a 'raw-dao' mode. it's the only distro that needs that. when i do that, it passed the media test, HOWEVER the installer *still* blows the install.  Debian Sarge, however, did install OK from netinstall.

---

### Post by cerulean coil on 2004-10-28
[QUOTE=Mighty Mik]... Ubuntu likes to be burned as a 'raw-dao' mode....[/QUOTE]

What's 'raw-dao'?

---

### Post by markw on 2004-10-28
[QUOTE=cerulean coil]What's 'raw-dao'?[/QUOTE]
 [http://www.google.com/search?hl=en&lr=&q=raw-dao+means&btnG=Search](http://www.google.com/search?hl=en&lr=&q=raw-dao+means&btnG=Search)

---

### Post by FLeiXiuS on 2004-10-28
What I would do is solve the network problem at first.  See why its not working (VIA console) and then solve the programs that were not installed.

Give me some details regarding your network.
Example: The use of routers/modems/cable/dsl/adsl/NIC Card.

---

### Post by im_ka on 2004-10-28
[QUOTE=cerulean coil]How do I do this? I'm downloading via my iBook, and I when I burn the iso I do check the box that says "Verify Burn". Is that the same?

Man, I'm a total newbie.  8-[[/QUOTE]

i can only tell you how to check the md5sum on under linux

---

### Post by cerulean coil on 2004-10-28
Perhaps this thread has the answer...

[Clicky.](http://www.ubuntuforums.org/showthread.php?p=8836&posted=1#post8836)

Basically, burn the iso to CD-RW at a slow speed *on a PC.*

[QUOTE=FLeiXiuS]What I would do is solve the network problem at first.  See why its not working (VIA console) and then solve the programs that were not installed.

Give me some details regarding your network.
Example: The use of routers/modems/cable/dsl/adsl/NIC Card.[/QUOTE]

Well, in good news, I did a slow (2x) burn to CD-RW, and that's worked much better; no missing packages, and I can log in under a Safe GNOME session. A normal session crashes, as before.

Signing into a normal session gets errors in GNOME Nautilus and Bonobo. Bonobo suffers from activation server error #3.

During boot up, I notice that Clock Sync fails, but that's due to not being connected with the net.

Booting into a safe GNOME session occurs in the same errors, but after they have been acknowledged, I get a message saying that "Desktop applet" had died, and asks if I want to delete it. I say no, and the message keeps coming up. *Until* I manage to get an application running before the desktop applet message comes back. Then I can run most programs normally, and the error stops coming up. The desktop is plain black. (Although I think thats because its a safe session rather than a normal bells 'n' whistles session.)

I even get the twinkly noises as it all boots up, which make me smile.  :-) 

Network wise, I do the install with the iMac disconnected from the net. I have no routers or anything, I'm going to sort that later. The iMac has an ethernet port, so if I stuck the ethernet cable my other computer is connecting to the net with, would that help? As far as I know, it has an ethernet card. Also, now that I'm using the CD-RW, during install it says "not connected, do you want to set up DHCP?" as opposed to "not connected, do you want to set up PPP?" during the CD-R install.

All in all, things are going much better. :D

Cheers for the help.

---

### Post by FLeiXiuS on 2004-10-30
YAY, Another happy Ubuntu user.  Always remember systems have faults when running to fast.  Slowing down never hurts. :-)  Glad to see you have gotten it working.

---

### Post by cerulean coil on 2004-10-31
[QUOTE=FLeiXiuS]YAY, Another happy Ubuntu user.  Always remember systems have faults when running to fast.  Slowing down never hurts. :-)  Glad to see you have gotten it working.[/QUOTE]

Semi-working. My Windows using friend is downloading the iso as we speak.

Fingers crossed, eh?

---

