---
title: "Question about OS updating"
date: 2014-03-14
forum: Installation &amp; Upgrades
---

### Post by dido2 on 2014-03-14
I'm about to install ubuntu on my personal computer,  but I cannot buy a DVD at the moment. So my question is - can I install an older version of ubuntu that fits on a compact disc and update it to the latest version available once installed? Thank you in advance. If you can link me an apropriate version of ubuntu that fits on a cd I'd be even more greatful.

---

### Post by howefield on 2014-03-14
I think the latest version to fit on a CD would be 12.04 (the current Long Term Support release supported till 2017) which you can get via ubuntu.com, this would then be upgradeable to the next LTS 14.04 when released next month.

---

### Post by dido2 on 2014-03-14
Thank you so much. Would you give me a link for pc version because when I was browsing in older versions menu I got really confused about the version I need. Im looking for a 32bit os. I saw some server editions or something and I got really confused. Im a total newbie when it comes to something other than Windows. Im typing from a phone because my internet connection on pc is messed upat the moment so Ill just download it on my phone and transfer/burn it on my pc. Thank you once again.

---

### Post by howefield on 2014-03-14
> **dido2 said:**
> Would you give me a link for pc version because when I was browsing in older versions menu I got really confused about the version I need.

The first link on this page [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/) is what you need, [http://releases.ubuntu.com/12.04/ubuntu-12.04.4-desktop-i386.iso](http://releases.ubuntu.com/12.04/ubuntu-12.04.4-desktop-i386.iso)

> Im a total newbie when it comes to something other than Windows.

I'm getting a bad feeling already :)

Please make sure all valuable data is backed up.

---

### Post by dido2 on 2014-03-14
Dont be. I dont have any data valuable or not on my pc. I just spotted that I have 12.04 on my pc and its 733mb which cannot be burned on a cd. Will check the links you gave me.
Yes its the same version. I cant burn that. Did you make a mistake or Im doing it?
Got 2 Maxell cds 700mb each and cannot buy a dvd now.

---

### Post by howefield on 2014-03-14
Apologies, I may be misremembering.

Are you aware that you can use a USB stick as an alternative to CD, or is that not an option either ?

---

### Post by dido2 on 2014-03-14
I am very much aware. Im not as stupid as you think. And yes, at the moment its not an option. Isnt it possible to find an lts version that fits on a cd?
Im sorry if my posts sound like a test for your nerves, but I thought I made it clear. Sorry again.

---

### Post by oldfred on 2014-03-14
I have not tried minimal. It is tiny as it just installs a kernel & Internet, so then you download the rest into your minimal install. Will be a lot more command line rather than gui install.

 [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
HowTo Achieve "Ubuntu-Desktop-Minimal" 
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)
Install script for minimal
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)
I had to add the line GRUB_GFXPAYLOAD_LINUX=text and voila, it works great! I also set GRUB_CMDLINE_LINUX=text instead of quiet splash. I think vt.handoff=7 was also causing problems. I'm thinking that this was necessary because the distro I'm using is "limited" or whatever it's called, command line only. Thus, maybe it was getting confused looking for a gfx driver or something.

 The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)

---

### Post by howefield on 2014-03-14
All desktop versions that predate 12.04.x are end of life and therefore unsupported and would be hard work taking them to a current LTS but that's not to say it can't be done. By hard work, I mean following the steps in this guide... [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

I suppose you could take the 32 bit version of [Lucid Lynx 10.04]("http://old-releases.ubuntu.com/releases/10.04.4/ubuntu-10.04.4-desktop-i386.iso") and using the above guide to upgrade to 12.04.

An alternative option might be to install using the [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") to get a base system and install whatever packages you need on top of that including desktop environment.

---

### Post by frank18 on 2014-03-14
> **howefield said:**
> Apologies, I may be misremembering.

Are you aware that you can use a USB stick as an alternative to CD, or is that not an option either ?

Don't be so sure to affirm that cause i have a Dell p4  and a sony vaio  that do not boot USB, only boot from cd.

---

