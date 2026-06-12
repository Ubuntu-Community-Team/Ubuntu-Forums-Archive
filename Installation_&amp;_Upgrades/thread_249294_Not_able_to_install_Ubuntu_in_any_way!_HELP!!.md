---
title: "Not able to install Ubuntu in any way! HELP!!"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by elijahclarity on 2006-09-02
Hi all

I'm DYING to install Ubuntu 6.06 but I have had no success in any way:(

Alternate CD:
When installing from Alternate CD, the screen goes blank  when it says, "Configuring xserver-xorg" and I'm forced to reboot.

Live CD:
The Live CD gives no better experience..when I select custom partitioning, and press Forward button, it always hangs and never goes beyond that.

This did not happen with Kubuntu & Xubuntu Live CDs and is only happening with the Ubuntu live CD. But alternate CDs of ALL 3 distros give the same result which I mentioned above. But I like Gnome & Ubuntu look more than Kubuntu/Xubuntu:( Dunno why its happenning with me!

Plz note that I want to do a clean install of Ubuntu 6.06....I know I can install ubuntu-desktop from the Ubuntu install CD if I'm using Kubuntu/Xubuntu but I don't want all that hassle....I want a clean lean install only of Ubuntu 6.06.

Plz help me out with this....as I REALLY REALLY wanna install Ubuntu dapper!!!

---

### Post by elijahclarity on 2006-09-02
Hardware info: Intel Celeron, 256MB RAM, Samtron 45Bn monitor...anythin else???

---

### Post by raptros-v76 on 2006-09-02
did you try verifying the install cd?
when the disk is booting, go to the option for checking the disk. burning iso's to disks can screw up easily enough to be a nuisance

---

### Post by taurus on 2006-09-02
I think you are experiencing a problem with your graphic card (and what it is anyway)?  Therefore, use the alternate CD to install it and don't worry about the error message about can't configure your X.  You can do that later after it finishes installing Dapper on your machine.  Then, you can reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by elijahclarity on 2006-09-02
I checked EVERYTHING....used the CDs which were shipped to me...verified md5sum n all that...no gain

---

### Post by elijahclarity on 2006-09-02
It never installs Ubuntu 6.06 in first place...when i reboot after the CD light has stopped blinking completely(after say half n hour)...i get a grub error!

---

### Post by Jenda on 2006-09-02
elijahclarity, how about trying to install Kubuntu anyway, and then carefully reworking it into Ubuntu - it's possible, and it's probably easier than anything else we could possibly suggest.

---

### Post by elijahclarity on 2006-09-02
No other way? :(

---

### Post by zxee on 2006-09-02
> **elijahclarity said:**
> No other way? :(

You said in an earlier response that dapper never installs-you get a grub error. > It never installs Ubuntu 6.06 in first place...when i reboot after the CD light has stopped blinking completely(after say half n hour)...i get a grub error!
Reply With Quote
Getting a grub error does not mean that dapper didn't install. It means that there's something wrong with how grub is being set up.

What disks and partitions do you currently have and which partition on which disk are you installing to? You may have an install from the alternate cd but are not able to boot into it., and that means you need to either re-install grub or fix it.
There are several specific ubuntu install guides here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)> 

---

### Post by s_26_c on 2006-09-04
> **elijahclarity said:**
> Hi all


Live CD:
The Live CD gives no better experience..when I select custom partitioning, and press Forward button, it always hangs and never goes beyond that.



The same problem crops up 4 me when I used the Live-cum -installer CD!!! Infact, I had to install Breezy at first, and then upgrade to Dapper!!Wonder what's the problem!!!

---

### Post by taurus on 2006-09-04
Try the server version and when install Gnome with

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

