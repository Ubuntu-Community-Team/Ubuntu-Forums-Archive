---
title: "Not Booting Correctly After Upgrading/Reinstalling 7.10"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by CLUGENHEIM on 2007-12-18
Hi. I had 7.04 and XP with dualboot, and finally decided to upgrade to 7.10. After doing so, I decided to do a fresh install of 7.10 instead for several reasons. (having installed tons of junk, etc.) But before I did, I tried booting 7.10. It didn't seem to work, as after the GRUB menu, all I got was a black screen. I didn't care because I was going to do a reinstall anyway. The problem is, after the reinstall, the same thing happened. =(

It always worked with 7.04, and the 7.10 Live CD works fine. I haven't left it at the black screen very long. Maybe 2-3 minutes, but it shouldn't take that long, and it shouldn't be a black screen. I'm reinstalling AGAIN as I type this to see if that helps or fixes anything, but I doubt that it will.

My computer specs: 
Fujitsu Lifebook
512mbs of RAM
1.73ghz processor (something like that)
60gb HD

Thanks in advance.

---

### Post by geek_Man on 2007-12-18
Reinstall Grub from the LiveCD... if that doesn't work then we can go through "the routine".

---

### Post by CLUGENHEIM on 2007-12-18
Uh, well, I just finished reinstalling 7.10 completely about 15 minutes ago, and discovered this: If I leave it at the black screen for like 5 minutes, it will FINALLY go to the log in screen. That's somewhat good news I guess. At least it works at all. I don't think it's got anything to do with GRUB either. I don't know anything though..

I'm going to download and install all the updates, as well as enable any restricted drivers, do a restart, and see if anything changes.

---

### Post by mukul_d on 2007-12-18
[FONT="Trebuchet MS"]I had this kind of trouble some time back with FC6. Is your computer on some network where authentication is coming from a central source like for example, AD or LDAP etc? I am asking this because I found out that disabling LDAP authentication in my boot-up fixed that problem. May be irrelevant but worth a look[/FONT]

---

### Post by CLUGENHEIM on 2007-12-18
> **mukul_d said:**
> [FONT="Trebuchet MS"]I had this kind of trouble some time back with FC6. Is your computer on some network where authentication is coming from a central source like for example, AD or LDAP etc? I am asking this because I found out that disabling LDAP authentication in my boot-up fixed that problem. May be irrelevant but worth a look[/FONT]

I don't know what you're talking about actually. How would I go about disabling it to give it a try? Updating everything and using allowing restricted drivers didn't help. =(

Any other ideas?

---

### Post by CLUGENHEIM on 2007-12-18
I've found a solution!

Not really. I'm just going to downgrade to 7.04. I've had several other problems with 7.10, and I'm getting sick of it. I never had these sort of problems with 7.04.

Thanks anyway.

---

### Post by mukul_d on 2007-12-19
Sorry for the delay and cryptic message.

I actually could not check out last night. I will check out tonight and let you know. And no, don't give up on 7.10.

I have to work on Windows in office so it has been when I reach home.

---

