---
title: "[nubuntu]Ubiquity crashes @ 94% (Installing/Configuring GRUB)"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by Andertraaks on 2010-02-25
Hi there. I've gotten hands on a nUbuntu Live CD and I so far I'm really liking it. So I was thinking of installing it onto my HDD, and therefor installed Ubiquity, and everything went smooth and painless until I hit 94% and it stops, pops up with an error message and after I click OK, it shows this:

[http://i48.tinypic.com/99jwoj.png](http://i48.tinypic.com/99jwoj.png)

and for a translation (With Google Translation):

[QUOTE=GoogleTranslate]We're sorry, the installer crashed. Please fill a bug report at https: / / launchpad.net / ubuntu / + source / ubiquity / + filebug (Do not add details to other existing error.) And a developer will look at the problem as quickly as possible. To help developers understand what is wrong look Include the following information and attach the files / var / log / syslog and var / log / partman:[/QUOTE] 
(I know I should file the report and I'm also going to, but I would ask if there is any quick fixes or anything related to that)

I've searched Google for parts of the error displayed in the pop up, but haven't really come up with anything.

PS: If I am posting in the wrong section, PLEASE mod, move my post instead of close/deleting it. Thank you.


Many thanks in advance,
Regards,
Andertraaks.

PS: God damn, I always forget this:
OS: nUbuntu 8.04 Alpha
Laptop: Acer Extensa 5220 (Part reason why I have a doubt that I'm posting in the wrong forum).

---

### Post by mörgæs on 2010-02-25
Nubuntu 8.04 er en gammel svend. Har du prøvet med en ny Ubuntu?

---

### Post by Andertraaks on 2010-03-03
> **mörgæs said:**
> Nubuntu 8.04 er en gammel svend. Har du prøvet med en ny Ubuntu?

Ikke for nyligt, var med indtil 9.04 kom, så skiftede jeg til Windows 7, men skal nok tilbage til at dual-boot mellem Ubuntu (Den nyeste må det blive) og Windows 7.

---

### Post by sam.reader on 2010-03-03
You are pretty lucky to have made it to 94%
I am not able to even begin the installation at all.
When I start installing the meter says 1% and stops.
When I press anything on the keyboard they system restarts.

---

### Post by RMau on 2010-03-03
I have the same issue. I think. I get to 94%, GRUB will not load, and I have a crash report telling me that Ubiquity 'closed unexpectedly'.

I'm trying to install on what was a Windows 7 machine. There are (2) HDs in a RAID 1 setup. I've tried with RAID enabled, and disabled on the motherboard. Nothing works.

I did notice I/O errors on the screen during the LiveCD boot. Something with a buffer error. I'll try to capture them in more detail when I have time to try this again.

If I try this again. This is the 2nd attempt, on two different machines, to install 9.10 that failed. The other one was a laptop that installed okay, but would not recognize the builtin wireless chip. I spent hours on that problem too, and finally just tossed the laptop back in the closet because nothing worked.

This is not fun, and shouldn't be this hard.

RMau

---

### Post by RMau on 2010-03-03
I completely dismantled the RAID setup in the system BIOS. I now have (2) independent 1 TB SATA drives. Ubuntu 9.10 finally installed without errors. But I don't have the RAID that I want and I'm not sure that both drives are 'seen' and usable.

However, I have the same problem with this desktop machine that I had with the laptop. The installed wireless does not work. The laptop has a RealTek chip, the desktop is using a Netgear adapter.

Shouldn't be this hard, and this time consuming.

RMau

---

### Post by mörgæs on 2010-03-03
> **RMau said:**
> ...and finally just tossed the laptop back in the closet because nothing worked.


You should rather toss 9.10 away. Try 9.04 and/or 10.04.

[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Though 10.04 is only an alpha it works surprisingly well. I guess we have a really good version coming up here.

---

### Post by mörgæs on 2010-03-03
[http://ubuntuforums.org/showthread.php?t=1404273](http://ubuntuforums.org/showthread.php?t=1404273)

---

