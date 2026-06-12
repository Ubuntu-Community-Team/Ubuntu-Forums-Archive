---
title: "Update causes hd corruption"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by mattinrom on 2007-12-20
I am running Ubuntu 7.10, i installed it from live. It listed 132 updates, i downloaded and during shutdown it said mount: / is busy, and when i started back up unclean and fsck ran, then fsck died and automatically rebooted, i narrowed it down to a linux-kernalimage update that gives a warning about assume lba32 could this be it? i cant use ubuntu it keeps corrupting so please help, ps its not my hardware as i am posting this from debian-sid with no issues.

---

### Post by mattinrom on 2007-12-20
no one, well thats ok since this system needs to be running, im going to go back to debian sid...thx anyway

---

### Post by PmDematagoda on 2007-12-20
You could be more helpful if you could **specify** exactly what errors you get. What error messages do you get?

---

### Post by mattinrom on 2007-12-21
"during the reboot it says / was unmounted cleanly and runs fsck, then fsck dies" ----
thats all i could observe, and it said fsck died, read the post i listed all the details i could.

---

### Post by PmDematagoda on 2007-12-21
Boot the PC using the Live CD, then try running fsck on the hard drive or partition in question.

---

### Post by mattinrom on 2007-12-21
Please read the entire post, theres nothing wrong with the hdd, i just loaded debian-sid and updated NO PROBLEMs its always right after updating ubuntu 7.10 and ONLY after the update

---

### Post by PmDematagoda on 2007-12-21
Yes, but it is an issue with fsck, we could give that a try and see if it is something with the drive or fsck itself.

---

### Post by mattinrom on 2007-12-21
BUT why is the drive corrupting after the update, fsck is ran when the drive corrupts, thats just a secondary issue, and when i build ubuntu from the xubuntu command line install, after the update and i reboot it says mount: root is busy, then the corruption occcurs

---

### Post by mattinrom on 2007-12-21
when i run fsck from live its clean, good, but if i install, get the 132 updates and reboot, well u get the picture. or if i install xubuntu-command line only system and apt-get ubuntu-desktop, i end up with an up to date desktop, theres 13 updates and when i get them BAM same thing

---

### Post by PmDematagoda on 2007-12-21
If Ubuntu Gutsy does not work, then you can also give Ubuntu Dapper (6.06) a try to see if you have better luck with it.

---

### Post by mattinrom on 2007-12-21
thats not a very good answer downgrade to a like 3 yr old OS, no thx, 7.10 used to work they just broke some random update, ill just used debian-sid becuse it updates and doesnt corrupt my disk

---

### Post by PmDematagoda on 2007-12-21
Well, whatever makes you happy, may be you can give Ubuntu 8.04 when it comes out on the April of next year.

---

### Post by mattinrom on 2007-12-21
I wont be trying 8.04 since sid is way more up to date and since ill have to invest about 12+ hours of time into compiling drivers and configuring X with support for compiz-fusion, i wont risk losing all that work.... im racking my brain trying to figure out tho what update caused the problem, it mightve been ext2 libs update....i use ext2...hmm but anywhos, a sad thing indeed, luved ubuntu too it was like using lenny + updates and compiz-fusion...hehe oh well

---

### Post by PmDematagoda on 2007-12-21
Why do you use ext2? That could be the issue you are having, maybe if you used ext3 you would have better luck.

---

### Post by mattinrom on 2007-12-21
no becuse i even tried reiserfs and it crashed even harder....it didnt even bother to run fsck so changing fs wont work

---

### Post by mattinrom on 2007-12-21
This is 100% non-hardware related, i know this for a fact.
Heres my exact routine:

Load ubuntu-gutsy gibbon 7.10 live
Install from live using ext2 (or reiser)
reboot
remove un-needed software
reboot again
update system

reboot (/ is busy)

then during boot fsck starts saying it is UNCLEAN, then it dies and reboots automatically

then i flip the bird to the pc, and reinsert said live disk.....
----

---

### Post by mattinrom on 2007-12-21
i saw a launchpad file about 64bit users getting a corrupt disk after getting 11 updates around nov 11, hm

---

### Post by mattinrom on 2007-12-21
Ok i did some backtracing and noticed that out of the 13 updates there is a linux kernal image, and during install it says warning: assume lba32, thats what may be causing my disk corrupting but why? and ps it happens on any drive with any fs... help

---

