---
title: "installing Ubuntu 7.10 on Dell Latitude"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by theunseenpen on 2008-02-01
I just purchased a used laptop with 60 gig's to install Gutsy onto, but so far I'm receiving an error with the initial boot of the live cd, and I'm wondering whether that'll lead to bigger issues later on...here's the error of which I'm unfamiliar with:

200.828000 Buffer I/O error on device fdo, logical block 0
238.936000 Buffer I/O error on device fdo, logical block 0
322.672000 Buffer I/O error on device fdo, logical block 0
360.776000 Buffer I/O error on device fdo, logical block 0

Any further advice would be greatly appreciated...

---

### Post by Rocket2DMn on 2008-02-01
Is there a floppy drive on the computer and is there a disk in it?  If there is a disk in the drive, take it out.
If you can still get to the Live session, you should be OK.

---

### Post by theunseenpen on 2008-02-01
thanks foremost of the immediate response but there was no disk in the drive and now as the live cd has finally loaded there's only half the page visible...I guess my graphics card is older than what is required to run Ubuntu? I'm able to load the installation window but I merely receive half of the box...so I can select which language at startup but unable to click continue/next to further the install...this sucks...but get this, winXP is already installed and it's functioning properly...what the heck? I've already installed Ubuntu on my main PC, and I just wanted to have it mobile ya know...I guess I wasted money on a laptop off of Ebay...[smirks]

---

### Post by Rocket2DMn on 2008-02-01
If the LiveCD is giving you graphics problems, you're in good company, a lot of people come here with issues.  You can install with the alternate cd which doesn't have a live session and is just a text installer which works very well.
You can get it at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box near the bottom for alternate cd.
If for some reason you still have graphics problems after install, those are relatively easy to fix.

---

### Post by theunseenpen on 2008-02-01
thanks again for this assistance...I have a slower connection currently so it'll take an hour to download the alternate disc...I'll be back on the forums in an hour or so to update you and those other faithful Ubuntuers...be well

---

### Post by theunseenpen on 2008-02-01
ok so far I've downloaded the text mode version of Ubuntu installer and I've gotten midway through it and now it won't install the base system and the rest of the process in now seemingly halted b/c of this main part of the system...I doubt my current CD-R disk is to blame...though I could be mistaken...any ideas?

---

### Post by Rocket2DMn on 2008-02-01
Did you check the md5sum on the iso file?
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against
You should also burn at a slow speed like 4x to prevent write errors.

---

### Post by theunseenpen on 2008-02-02
Well Rocket2DMN, I've got it installed and am now attempting wireless, though I figured a simple USB Netopia adapter would do for a lil'while until I purchased a proper PCMCIA card but it's not being recognized. This laptop is about four/five years old now, but I think a cheap wireless card from Wally World would suffice...am I right? I hope so because by the time you or anyone else reads this I'll probably be well on my way homeward with the card...be well.

---

### Post by lnk5700 on 2008-02-02
> **theunseenpen said:**
> ok so far I've downloaded the text mode version of Ubuntu installer and I've gotten midway through it and now it won't install the base system and the rest of the process in now seemingly halted b/c of this main part of the system...I doubt my current CD-R disk is to blame...though I could be mistaken...any ideas?

but how do you say that?

---

### Post by Rocket2DMn on 2008-02-02
Have a look here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

