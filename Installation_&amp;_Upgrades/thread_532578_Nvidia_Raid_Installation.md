---
title: "Nvidia Raid Installation"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by gotmonkey on 2007-08-22
I am a little lost on this one. I have an EVGA NF41 mobo with 1x200gig Sata and 2x500 Sata drives. I set the onboard nvidia raid controller to mirror, I am planning to use the 500gig drives as a mirror. When I started to install Fiesty Fawn (7.04), It showed me a list of the drives on my system. It listed out all three of the drives. What do I need to do to get Ubuntu to see the mirrored 500gig drives as a mirror (Single 500gig drive). 


Thanks

---

### Post by Pumalite on 2007-08-22
[http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

[http://www.howtoforge.com/forums/showthread.php?t=2094](http://www.howtoforge.com/forums/showthread.php?t=2094)

[https://launchpad.net/ubuntu/+source/grub-installer/+bug/17404](https://launchpad.net/ubuntu/+source/grub-installer/+bug/17404)

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by gotmonkey on 2007-08-22
> **Pumalite said:**
> [http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

[http://www.howtoforge.com/forums/showthread.php?t=2094](http://www.howtoforge.com/forums/showthread.php?t=2094)

[https://launchpad.net/ubuntu/+source/grub-installer/+bug/17404](https://launchpad.net/ubuntu/+source/grub-installer/+bug/17404)

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Thanks, I am looking at them right now. I have ubuntu installed on the 200gig drive. I want to make the 500gigs as the raid mirror. I think the FakeRaid link might have the best information, unless you have a better suggestion. 

Thanks

---

### Post by Pumalite on 2007-08-22
No; that's the best and most recent one. I wanted to give you a historic perspective.

---

