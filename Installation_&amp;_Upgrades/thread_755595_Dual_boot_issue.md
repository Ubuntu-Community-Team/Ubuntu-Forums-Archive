---
title: "Dual boot issue"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by Kabezon on 2008-04-15
Hello =] I have a really annoying issue when it comes to dual bootin! Well, here' s the way I did it: Using a Win XP CD I formated my whole HDD, then created 2 partitions, a 70GB one and a 300GB one. Then, I installed Win XP on the 70GB partition, worked like a charm, as a matter of fact I'm on Win XP ATM. Then, I run the Ubuntu 7.10 Live CD and tried to install it in the 300GB partition, but here comes the problem:  It just WON'T! Installer has an error copying files :S The reasons might be that I'm using a bad copy, that the CD or the CD Drive is dirty, or that the HDD has problems. Well, since I already tried with 3 different Ubuntu CDs and my PC is relatively new, I guess the HDD is the one causing this issue. Did I do things completely wrong? Is this the way to make dual boot?  And, oh, yeah, almost forgot, managed to install Kubuntu, it gave me an error about the sources.list, but I manually fixed that, still, eveyrthing was buggy! Even though I installed missing dependencies and stuff, things just didnt work! And then, yesterday, I turned on my PC and tried to boot it... wont go past login screen! I type my password, press enter, screen goes black for 5 secs, and then the login screen reloads :S! Help me please :(

---

### Post by Partyboi2 on 2008-04-15
after you had downloaded ubuntu did you check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")? Burning the iso at a low speed like x4 or less is recommend to aviod a bad burn. Also check the cd for defects (one of the options at the main menu)

---

### Post by garfonzo on 2008-04-15
The only thing I would do different is this (and I've done it):

1. Reinstall WinXP on the WHOLE drive, yes, no partitioning... yet. 
2. Then, once you have WinXP living happily on that large drive, boot from the LiveCD (a new one, as mentioned before, burning slowly).
3. Don't install yet, but rather open up the Disk Partitioner (GParted?) which is one of the menus at the top (writing this post in Vista, can't remember the names)
4. Resize your WinXP partition down to 70GB and leave the remaining disk empty and apply changes. 
5. NOW go for the install icon on the desktop. Install on the remaining space (you'll get that option, which I'm sure you know).

I have no idea what is causing your problems but, this is the method I have used a number of times. I don't know if it will give you better results, but it would be worth a try.

EDIT: Oh, and if you aren't getting an error message during the install, but rather it just seems to hang without activity, just WAIT. I've had it 'hang' for quite some time, but because I wasn't paying attention to it, it finally figured out whatever it was doing, and finished. So, it may appear to have failed, but really it is just thinking about its next move ;-)

Cheers,

Garfonzo

---

