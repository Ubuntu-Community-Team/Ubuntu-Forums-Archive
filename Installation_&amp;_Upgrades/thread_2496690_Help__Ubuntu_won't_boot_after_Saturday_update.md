---
title: "Help:  Ubuntu won't boot after Saturday update"
date: 2024-04-08
forum: Installation &amp; Upgrades
---

### Post by BeachNerd on 2024-04-08
Using the latest release of Ubuntu (23.10 - I think) on older (8 years ?) HP Laptop.  After proceeding with update (I had received a notification that an update was available on Saturday), the update appeared to have installed, but after rebooting (can't remember if I rebooted or it rebooted on it's own) I get a 'sad face' screen.  I did try the limited GRUB menu 'repair' options available but no change.  Just wondering if there's something obvious I can do before resorting to reinstalling ubuntu.   I apologize for the limited specific information in this post but I'm posting this from another computer (and not currently at home).

---

### Post by Impavidus on 2024-04-09
I'm not familiar with a skull and crossbones screen. It almost sounds like a software pirate trying to be funny.

With a live disk you can investigate the logs, see what upgrades were installed, look for anything suspicious, make backups of your files (if you haven't got those already). I can't say for sure whether you've got a big problem or a small one, but if I were in such a situation, I'd just reinstall.

---

### Post by MAFoElffen on 2024-04-09
Do you have backups?

---

### Post by BeachNerd on 2024-04-09
> **Impavidus said:**
> I'm not familiar with a skull and crossbones screen. It almost sounds like a software pirate trying to be funny.
.

Sorry, my bad - not skull and crossbones - a sad face:

[IMG]https://i.imgur.com/gNcnfRV.jpeg[/IMG]

---

### Post by BeachNerd on 2024-04-09
> **MAFoElffen said:**
> Do you have backups?

Not that I'm aware of.  It's a relatively new installation (over the last couple of months) and I hadn't got around to actually using the laptop for anything.

---

### Post by Impavidus on 2024-04-09
That looks less suspicious. If that last update included a kernel upgrade, you could try booting an older kernel. Reading the logs may give a clue about what went wrong. But given that you haven't really used the system yet, a fresh install should take only half an hour or so. If, after installing the upgrades after the install, you get the same issue, you'll know for sure it was caused by an upgrade. Then you can figure out what upgrade causes the problem and file a bug or find some workaround.

---

### Post by ubfan1 on 2024-04-09
I got that screen too after a nobel (24.04) VM update/upgrade.  The upgrade was for hundreds of packages, but half were being held back.  The next day, a boot of the VM showed the unhappy face.  I just redownloaded the nobel iso (which failed many times, and gave up a few times for extremely low bitrates, but later that day, the download worked and a reinstall had all working again.  I figured some temporarily glitch related to the xz issue, but don't know why 23.10 would have been affected.

---

### Post by BeachNerd on 2024-04-09
> **ubfan1 said:**
> .... The upgrade was for hundreds of packages, but half were being held back.  

I experienced the same thing.  Was advised that not all of the updates could be downloaded and asked if I wanted to proceed with the ones that could be downloaded.  Maybe I should have chosen NO.

---

### Post by ubfan1 on 2024-04-09
Definitely improvements can be made when holding packages back (or phasing).  A  group of packages that need to be together may be separated, and break things.  I have only seen this on a group of Nvidia packages -- one was held back, and the module rebuild failed.  The next day, that package was released and module building worked.

---

### Post by BeachNerd on 2024-04-10
I gave up troubleshooting and reinstalled Ubuntu. Took a while and had to go through the setup again but all appears stable at this point.  One thing I don't get is: when I turn it on, I get a windowed message that an application is requesting access to the key ring (i.e. it's asking for the pasword).  I didn't get that on the old install (there was a user login screen) and both installs were from the exact same install DVD (23.10).

---

### Post by yancek on 2024-04-10
You can install very differently by choosing different options using the same media (DVD/USB).  I"m not familiar with keyrings but you might try reading through the page at the link below discussing its use on Ubuntu.  Else try an online search for using keyring on Ubuntu.

[https://itsfoss.com/ubuntu-keyring/](https://itsfoss.com/ubuntu-keyring/)

---

### Post by BeachNerd on 2024-04-10
> **yancek said:**
> You can install very differently by choosing different options using the same media (DVD/USB).  I"m not familiar with keyrings but you might try reading through the page at the link below discussing its use on Ubuntu.  Else try an online search for using keyring on Ubuntu.

[https://itsfoss.com/ubuntu-keyring/](https://itsfoss.com/ubuntu-keyring/)

Thanks for that link.  That's exactly what I'm seeing.

---

### Post by granthjones on 2024-04-19
I've got a similar problem here, on 4/19 I ran apt update/upgrade (It'd been about a week) it took (wants to) the kernel from -102 to -105 but now it won't boot.  I can select -102 from the grub menu and that'll boot.  I'm a newbe to ubuntu/linux and really don't have any idea other than it looks to be related to the new kernel.  I get an "Invalid Magic Number" error then it says "You need to load the kernel first."  I've been poking and Googleing around and stuff but still haven't got it to work.  Anyone got any comments?  Thanks.

---

