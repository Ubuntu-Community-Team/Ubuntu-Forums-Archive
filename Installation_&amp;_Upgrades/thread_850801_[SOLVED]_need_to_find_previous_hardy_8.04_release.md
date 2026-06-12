---
title: "[SOLVED] need to find previous hardy 8.04 release"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by neysito on 2008-07-06
Hi everyone:
I have been struggling for 16 hrs trying to install the new Ubuntu release and getting all sort of “SQUASHFS errors” and/or “Buffer I/O errors” as well, I have tried many different boot commands without finding the right one/combination that I might work on my pc . It seems that for some reason this new installer does not like the Jmicron controller in my ASUS P5K motherboard, which it used to be just fine before.
Can anyone point me please to where I can download the previous release 8.04 (not 8.04.1) so I can at least install without any problems (already worked before) and update/upgrade later. I cannot find it on the mirrors anymore

I just gave up on this one.

Thanks in advance

---

### Post by Sef on 2008-07-06
Did you run 'check disk for errors' instead of trying to install/boot into the live cd?

---

### Post by neysito on 2008-07-06
No, I actually did not, instead i downloaded the iso from 2 different mirror just in case and it was the same pain with both, but it will be the first next move i make for sure.
Thanks a lot for your pront reply

---

### Post by confused57 on 2008-07-06
> **neysito said:**
> Hi everyone:
I have been struggling for 16 hrs trying to install the new Ubuntu release and getting all sort of “SQUASHFS errors” and/or “Buffer I/O errors” as well, I have tried many different boot commands without finding the right one/combination that I might work on my pc . It seems that for some reason this new installer does not like the Jmicron controller in my ASUS P5K motherboard, which it used to be just fine before.
Can anyone point me please to where I can download the previous release 8.04 (not 8.04.1) so I can at least install without any problems (already worked before) and update/upgrade later. I cannot find it on the mirrors anymore

I just gave up on this one.

Thanks in advance

May not be your problem, but see my post in this thread:
[http://ubuntuforums.org/showthread.php?t=849915](http://ubuntuforums.org/showthread.php?t=849915)
I would recommend trying the alternate install cd.

---

### Post by neysito on 2008-07-06
Thanks for your help confused57

I actually downloaded and burned the cd twice on the same pc where i was trying to install ubuntu, from a separate vista partition and also using nero but it just didn't work for me.

During my painfull proccess today i read you thread like 6 times

---

### Post by confused57 on 2008-07-06
> **neysito said:**
> Thanks for your help confused57

I actually downloaded and burned the cd twice on the same pc where i was trying to install ubuntu, from a separate vista partition and also using nero but it just didn't work for me.

During my painfull proccess today i read you thread like 6 times
I feel your pain...the IDE controller on my Gigabyte mobo is JMicron.  Have you tried the alternate install cd, or downloading and burning the iso on another computer?  I have concluded that it may some kind of incompatiblity with my new DVD writer in the Gigabyte pc, which I just built recently and running the DVD's written from it is causing problems on other DVD drives.
Good Luck with it.

Added:  Found someone else with the same problem who used the minimal cd to install Hardy:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by neysito on 2008-07-06
First of all thanks to evereyone for your help!!!

I managed to install 8.04.1 by downloading and burning the iso image in a diferent computer with a diferent burner and on a diferent brand of media CD, I don't really know wich one was causing the problem to my two DVd Burners to read the CD properly, but at least it made all the difference and my pc was able to read the installer and run it all the way without anymore dificulties at all.

Typing now from my brand new 8.04.1 install.

I hope this can help others with similar install problems

---

### Post by confused57 on 2008-07-07
> **neysito said:**
> First of all thanks to evereyone for your help!!!

I managed to install 8.04.1 by downloading and burning the iso image in a diferent computer with a diferent burner and on a diferent brand of media CD, I don't really know wich one was causing the problem to my two DVd Burners to read the CD properly, but at least it made all the difference and my pc was able to read the installer and run it all the way without anymore dificulties at all.

Typing now from my brand new 8.04.1 install.

I hope this can help others with similar install problems

Glad you were able to get it working...there's nothing wrong with the 8.04.1 iso image, it's definitely a DVD writer/hardware/cd-media(?) incompatiblity of images written to disk on my Gigabyte machine with my other pc's.  Burned a disk of PCLinuxOS_2007 on the Giga pc, would only boot on it, not on the other pc's that I have. 

 Yes, hopefully this might help other users with similar problems.

---

