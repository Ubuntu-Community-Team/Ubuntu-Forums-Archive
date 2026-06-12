---
title: "Can't Install the !! Thing!"
date: 2005-11-28
forum: Installation &amp; Upgrades
---

### Post by Empeda on 2005-11-28
Hi, I'm a realtive novice with Linux though I have used it in the past...

I've got the free CD installation disk for v5.04.

It starts okay, mounts the cd-rom etc, but when it get to the bit where it's installing additional components, it gets to 34% and then just stops.

I've tried server, expert and various over options and I'm at my wits end! The web site is very unhelpful aswell....

Has anybody else had the same problem or can anyone help? 
Cheers!:confused:

---

### Post by aysiu on 2005-11-28
Sounds like a bum CD.
Did you [check the disk image before burning it](http://www.linuxiso.org/viewdoc.php/verifyiso.html)?
Did you burn it at a slow speed (2x or 4x)? Hint: you should.

---

### Post by Empeda on 2005-11-29
Hi thanks for replying - sorry about the tone of the post it was late last night!

It isn't a bum CD as it's one of the shipped ones - I didn't burn it, and I've got ten copies of it, so I've tried multiple CDs and the same thing happens everytime - installing the additional bits and it gets to 34% and stops.

In expert mode I can bypass this part but I figure it's pretty integral as I cannot install the base system without it by the looks of things.

I'm using a fairly old Toshiba Laptop (2000) which did have Win98 on it before I wiped it. I can't remember the exact model but it's got 32mb of RAM  and a 6GB hard drive so the spec should be fine for Ubuntu. It does however say that it's installing in low memory mode everytime mind....

---

### Post by dubz on 2005-11-29
Are you aabsolutely surenothing is happening.
What package is being installed?

with only 32MB of RAM stuff could take a very long time

---

### Post by parktownprawn on 2005-11-29
not all the ubuntu ship-it cds are good - i've had experience with one or two dud cds from them - maybe they got damaged in the mail or maybe they where bad burns to start with.  i would try a different cd.

---

### Post by Empeda on 2005-11-29
Hi all!

I've got ten copies of the shipped CD and I've tried 3 different ones and they all do exactly the same thing.

It gets to 34% and then the screen goes black, and the same progress bar comes up again - but beginning for 0%. It then gets up to 1% and does exactly the same thing again. It then does this 7/8 times before just sticking on the black screen forever.....:(

---

### Post by PMO6022 on 2005-11-29
[quote=Empeda]I'm using a fairly old Toshiba Laptop (2000) which did have Win98 on it before I wiped it. I can't remember the exact model but it's got 32mb of RAM  and a 6GB hard drive so the spec should be fine for Ubuntu. It does however say that it's installing in low memory mode everytime mind....[/quote] I have tried to install ubuntu on an old toshiba satellite 2505 cds with only 32 mb of ram and had the exact problem you describe.  The install progresses, and then just restarts at the same % complete each time.  If you go to the error tty (alt - f3 or f4, I believe) during the install process you will likely see that you are running out of memory.  I ran out of memory during a minimal server install as well.  I think there were too many modules being loaded (such as for the IR port, etc.)  I tried paring down the install, I tried installing straight debian, and the only thing I could get to work was slackware.

I think you are most likely running out of memory.  If that is the case, you will probably have a hard time getting ubuntu installed.  I suggest either buying another stick of ram or installing a different distro.

---

### Post by Empeda on 2005-11-29
Thanks for that mate - I've got a copy of SuSE that I might try instead - I can still play with Ubuntu live on my main system....

thanks for all the help everyone!:p

---

### Post by cannuck on 2005-11-29
I got it to install Live CD on IBM laptop - whenever it stalled on the start up - I just pressing enter multiple times. However it won't actually run - after the start up process.

---

### Post by parktownprawn on 2005-11-29
[QUOTE=Empeda]

thanks for all the help everyone!:p[/QUOTE]

well my first advice was useless since i hadn't read you post properly but I can try redeem my self by suggesting a light linux distribution:
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

its a pretty small download - "only" 50M

---

### Post by Empeda on 2005-11-30
Thanks mate, yeah I 've heard of that one - I've actually discovered a version of Slackware I forgot I had so I've sucessfully installed that - now I'm playing ;)

---

