---
title: "amsn+upgrading from 7.10=royally screwed up OS installation"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Grrblt on 2008-04-24
Just now I tried to upgrade to 8.04 from 7.10 (normal ubuntu with no x or k or anything in front). My upgrade window thingy downloaded the stuff and started chewing on installing. I didn't see a "don't do other stuff at the same time" warning sign so I went ahead with my business. Maybe 5 minutes into the actual installation, I decide to change my profile picture in aMSN. I click the "Browse" button and BAM! I'm thrown out to the login screen. When I log in, I get that a screen with that brown background and a mouse pointer. Nothing happens from there :(

I realize I probably did something I shouldn't have with that Browse button in aMSN, and I also realize I probably need to wipe the linux partition and do a complete reinstall now. Good thing I'm still a windows user (WOW DID I REALLY SAY THAT!? :D) and didn't really have that much stuff on linux yet. Just thought I'd let you clever programming guys know so you can fix it (or boink the aMSN programmers to fix it if it's their fault).

---

### Post by Ub1476 on 2008-04-24
Go to sessions and select the failsafe terminal. If it works, run these commands:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

I also suggest Emesene as an IM;)

---

### Post by Grrblt on 2008-04-24
well, how about that. I misunderstood what you said and typed that stuff in in recovery mode instead. It didn't exactly work and when I realized what you meant by sessions, I rebooted only to find that the sessions thing wasn't even there on my login screen anymore :(


and I looked with interest at Emesene until I noticed it didn't have webcam.

---

