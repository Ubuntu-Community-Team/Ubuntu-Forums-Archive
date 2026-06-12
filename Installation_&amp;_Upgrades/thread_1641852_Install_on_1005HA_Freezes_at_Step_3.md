---
title: "Install on 1005HA Freezes at Step 3"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by JetBlk on 2010-12-09
I am trying to install 10.10 desktop version from a usb stick on my ASUS EEE 1005HA netbook and when I get to the keyboard step, it locks up instantly when I select my keyboard and proceed. I've searched around google for a solution but can't seem to find one that works. I've messed with the bios settings, reset them etc, checked the image on the usb and everything as well. No matter what I do it just freezes at that step. ctrl+alt+f1 does nothing as well, completely locked down until i do a hard reboot. I've also waited until it says "Ready when you are..." before selecting the keyboard and continuing. Also i'm trying to do a clean install, had backtrack4 on it previously.

How can I fix this or get it to install successfully?

Thanks!

---

### Post by JetBlk on 2010-12-10
*bump* Any ideas? :\

---

### Post by sikander3786 on 2010-12-10
Welcome to the forums :-)

You mentioned you've checked the image but did you also check the disc for defects.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

Before some-one else comes with some better suggestion, and if the disc is ok, I would recommend to press F6 at the same screen (boot screen mentioned in the link above) and try adding some boot parameters. There are 6 of them and you need to try all of them one-by-one.

---

### Post by JetBlk on 2010-12-10
Yeah the disk was ok, I'll have to try the boot parameters when I get out of work later. Thx for the suggestion :)

---

### Post by tribos on 2010-12-10
> **JetBlk said:**
> I am trying to install 10.10 desktop version from a usb stick on my ASUS EEE 1005HA netbook and when I get to the keyboard step, it locks up instantly when I select my keyboard and proceed. I've searched around google for a solution but can't seem to find one that works. I've messed with the bios settings, reset them etc, checked the image on the usb and everything as well. No matter what I do it just freezes at that step. ctrl+alt+f1 does nothing as well, completely locked down until i do a hard reboot. I've also waited until it says "Ready when you are..." before selecting the keyboard and continuing. Also i'm trying to do a clean install, had backtrack4 on it previously.

How can I fix this or get it to install successfully?

Thanks!

I have the same problem trying to install Mint 10 on an Acer Aspire 1 D150, I tried to make dual Linux (Mint 8 & 10) and then tried a clean install... hung at the same point both times. 

Cheers, S

---

### Post by tribos on 2010-12-10
Looks like answer is here, but server seems down at the moment...  [http://forums.linuxmint.com/viewtopic.php?f=46&t=59959&start=0](http://forums.linuxmint.com/viewtopic.php?f=46&t=59959&start=0)

---

### Post by tribos on 2010-12-10
> **JetBlk said:**
> Yeah the disk was ok, I'll have to try the boot parameters when I get out of work later. Thx for the suggestion :)

Username -> username   (can't start with a capitol letter)

---

### Post by sikander3786 on 2010-12-11
> **tribos said:**
> Username -> username   (can't start with a capitol letter)
Thats right. It is a bug in 10.10 installer that it doesn't throw an error when there are some invalid characters in username field. It just greys out forward button and stays there. However fixed in 11.04 installer.

Simply, username can't contain capital letters or spaces ;-)

---

### Post by JetBlk on 2010-12-12
well, i havent even got the chance to enter a username yet so thats not the problem. also tried the boot options, did nothing :\

---

