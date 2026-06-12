---
title: "Dual Boot 12.04 &amp; Windows 8 on Dell XPS 8300"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by Dyme21 on 2012-11-23
So for a while now I've been trying to dual boot windows and Ubuntu on my dell XPS 8300, but I always have trouble when it comes to partitioning.

I burned the 12.04 64-bit iso to an empty CD and booted off of it. I then clicked "Try Ubuntu" and connected to wifi. Next I opened up the install wizard completed everything perfectly until I got to this screen ([http://i.imgur.com/UkIb3.jpg](http://i.imgur.com/UkIb3.jpg)). Based off of many install guides and tutorials I have read I was expecting a "Install Alongside Windows" option but none was available. I then proceeded to select "Something else" to look at my partitions ([http://i.imgur.com/zub4C.jpg](http://i.imgur.com/zub4C.jpg)).

Here is the part I'm confused with and I want to make sure I'm doing everything right so nothing gets messed up.

The installer shows me that I have one 1TB drive divided into three partitions. In reality, I have two 500GB drives. Gparted says the same as the installer ([http://i.imgur.com/S6jcx.jpg](http://i.imgur.com/S6jcx.jpg)). After doing a little research, I found that I have some sort of software called "RAID" that is doing this.

So finally my question to you is: "How can I safely dual boot Windows and Ubuntu with this setup?" Keep in mind that In reality I have two 500GB drives being connected with RAID.

Below is some more information on my system that I got from Speccy and Windows Disk Management Tool. Thanks for your time and support.

Windows Disk Management - [http://i.imgur.com/x8siw.png](http://i.imgur.com/x8siw.png)
Speccy Hard Drive Info - [http://i.imgur.com/Ycz3A.png](http://i.imgur.com/Ycz3A.png)
Speccy General Info - [http://i.imgur.com/BWzXp.png](http://i.imgur.com/BWzXp.png)

---

### Post by Futant on 2012-11-23
Can't help you with technical details, but with the few (about 6) 'buntu installations I've done I've found that the installation is smoother if you choose to 'install without trying first' or whatever it says, rather than using the installer in the live session... Couldn't say why, and it may be an illusion anyway :-P

---

### Post by Dyme21 on 2012-11-23
> **Futant said:**
> Can't help you with technical details, but with the few (about 6) 'buntu installations I've done I've found that the installation is smoother if you choose to 'install without trying first' or whatever it says, rather than using the installer in the live session... Couldn't say why, and it may be an illusion anyway :-P

Just tried it, nothing seemed to be different though :(

Thanks for the reply though.

---

### Post by oldfred on 2012-11-24
Installing with RAID is only supported with the altnerative or server installs with 12.04. 12.10 does not have an alternative installer and they wanted it to do everything that alternative would do, but did not finish.
       Elimination of Alternative installer for 12.10 and no RAID support directly for Desktop.
[http://ubuntuforums.org/showthread.php?t=2049021](http://ubuntuforums.org/showthread.php?t=2049021)

    
You have to add the RAID drivers in the liveCD to correctly see the RAID partitions, but I do not think that helps the installer.
       sudo apt-get install mdadm
    
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

