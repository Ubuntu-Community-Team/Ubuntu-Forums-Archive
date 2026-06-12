---
title: "Install hangs at 15%"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by acidblue on 2007-04-27
Just got the 7.04 fiesty from OSDisk I tried to do an install
but got this problem with fiesy seeing my only disk in my
Toshiba Tecra 9000 as sda instead of hda i unpluged all external
drives.
So i tried to do an install anyway but it hangs at 15%, the drive will 
spin the disk for  few minutes and sounds like it's installing but my 
hard drive  led isn't blinking and then it will stop for a minute  or two 
then restart but no blinking led.
So i let it go for about a 1/2 an hour--didn't install just hangs at 15%
even though the disk is spinning, just dosn't transfer to hard drive.

Is there a way to fix this?

---

### Post by HansKloss on 2007-04-27
Are you sure it is not a defective CD?  Try burn it again.
How about installing in safe graphic mode?
Any error messages? ctrl+alt+F1...F8 should give access to the console
Look for any errors check dmesg output

---

### Post by ydoucare on 2007-04-27
I had that EXACT same problem.  Install would hang at 15%, and the CD would spin up and spin down almost in a loop for a while, with no HD activity.  This was on a Toshiba Satellite 5005 (old laptop).

Eventually, I got it to work, but i'm really not sure why it even worked, because all I did was load the system monitor, then start the install, only so I could monitor memory usage.  Install went fine after that.  This is after I attempted to install probably 3 times already with 2 different burns.

---

### Post by acidblue on 2007-04-28
Yes i tried that, but unforntunatly my system would run hella slow after i started the System Monitor.
I mean painfully slow, so  slow i couldn't take it anymore, and my mouse would lock-up.
I think it's something to do with older Toshiba laptops.

Edit: 
I don't have cd burner, i bought the disk at OSDisk.
ummm..... install in safe graphic mode, never thought of that.
i'll give it a try.

---

### Post by acidblue on 2007-04-29
Ok i tried everything, still hangs at 15%
I really thought booting into 'safe graphic' mode would do it, but no.
I'm about to give up and install Mandriva--even though i hate there pkg mngr system

---

### Post by Ciego on 2007-04-29
Many people have been having this problem installing Feisty on the PS3.  Our solution was to kill any unnecessary processes and then install.

See the discussion thread in the PSUbuntu forums.

[http://psubuntu.com/forum/viewtopic.php?t=274](http://psubuntu.com/forum/viewtopic.php?t=274)

---

### Post by acidblue on 2007-04-29
ok i got it installed but now i have a different problem.
Grub didn't seem to install, when i do a reboot i get a grub> prompt.
So how do i reinstall grub--to mbr.

---

### Post by Ciego on 2007-04-30
I would suggest trying the alternate install cd.  I had the same issue with grub not installing and the alternate cd      fixed the problem.

---

### Post by acidblue on 2007-04-30
Ok I got it to install here's what i did:
This is going to sound lame but it worked, i reset the system clock to the correct timezone.
I noticed the time in the panel was wrong so i set it, it was set to New York time zone, i just 
set to my correct zone, LA.
After that i tried to install and WOLA! it worked.
However after a reboot i had a very slow system, the mouse was erradic and i had a blank screen.
So i rebooted into 'safe mode'got a cmmd prompt and did as root(sudo) dpkg-reconfigure xserver-xorg>> and now evrything is fine! 
But in the future i think i will get the alternate install cd

---

### Post by mwiebelhaus on 2007-04-30
usually at 15 % it will tell you about something about swap disk or phiyscal memory if you haven't done it , but that is for 6.02

---

