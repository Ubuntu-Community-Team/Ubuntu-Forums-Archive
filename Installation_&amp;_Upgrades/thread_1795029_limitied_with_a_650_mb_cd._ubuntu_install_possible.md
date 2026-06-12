---
title: "limitied with a 650 mb cd. ubuntu install possible?"
date: 2011-07-01
forum: Installation &amp; Upgrades
---

### Post by azitizz on 2011-07-01
I have a cdr and a computer I would like to install ubuntu on or at least get a live cd running. I only have a 650mb cd-r though and the computer wont support usb booting. 

Anyone have any suggestions as to how that can be accomplished? I cant boot into windows either on the comp I wish to install Ubuntu. I plan on making it a Ubuntu-only computer as the windows is old and password protected by users long gone. Im ready to wipe it clean with a new install of Ubuntu.

---

### Post by nitstorm on 2011-07-01
You can use a Minimal Ubuntu install and then use the Network connection to upgrade your packages and also install the full Ubuntu Desktop

[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

---

### Post by azitizz on 2011-07-01
> **nitstorm said:**
> You can use a Minimal Ubuntu install and then use the Network connection to upgrade your packages and also install the full Ubuntu Desktop

[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

Thank you. I think I was looking for just that and found it as you replied. I hope it works. All depends if the old clunker can handle the latest ubuntu. It would be nice if it did but Ill see.

---

### Post by MAFoElffen on 2011-07-01
> **azitizz said:**
> I have a cdr and a computer I would like to install ubuntu on or at least get a live cd running. I only have a 650mb cd-r though and the computer wont support usb booting. 

Anyone have any suggestions as to how that can be accomplished? I cant boot into windows either on the comp I wish to install Ubuntu. I plan on making it a Ubuntu-only computer as the windows is old and password protected by users long gone. Im ready to wipe it clean with a new install of Ubuntu.
Sort of a round about way...

All the Stanard images of Ubuntu Natty are larger that 650MB.  But there are some offshoot distributions of Ubuntu- Kubuntu, Xubuntu and Lubuntu.  Then there are subsets that they are based on...XFDE and LXDE.  The alternate install Cd of Kubuntu is just about 650MB.  Xubuntu and Lubuntu are historically smaller and leave a smaller footprint, but...

If you visited the below link and downloaded the LXDE LiveCD:
[http://lxde.org/download](http://lxde.org/download)
It is only 453MB...

Then after installing, opened a terminal and
```

sudo apt-get install ubuntu-desktop

```I'm thinking it should install Ubuntu on the base...  As long as it had the software sources pointed in the right direction.  If it didn't, post back and I'll post the software sources it would need.

---

