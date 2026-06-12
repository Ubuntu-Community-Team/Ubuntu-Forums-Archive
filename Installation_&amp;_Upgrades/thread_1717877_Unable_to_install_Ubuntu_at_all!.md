---
title: "Unable to install Ubuntu at all!"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by JTallis on 2011-03-30
These are serious issues which have, well pretty much ruined my week.

First I tried a liveCD, and this says "Unable to find a medium containing a live file system".

I then tried the windows installer, and this says "Unable to find Installation Iso: path/to/installation.iso" - I don't remember the exact path but I did double check and the iso was indeed there.

I tried a liveUSB, and this refused to boot. Just booted up in Windows as normal and I did change the boot order.

What did work is when I had the liveCD in AND the liveUSB. It booted from the liveCD and believed the liveUSB was it's live file system from my understanding.

Though, during this - it was unable to detect my hard drive. The installation couldn't find any allocated space and when I ran the demo, it was unable to find any drives at all. Not even my disk drive!

I tried to recreate the liveUSB but with no luck.

I need some help, please. Thanks!

---

### Post by Rubi1200 on 2011-03-30
Hi,

it sounds as if there might be an issue with the downloaded image.

Try this:

1. post the specifications for the computer

2. check the integrity: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

3. burn to CD at the lowest speed: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

For USB, I recommend UNetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by coffeecat on 2011-03-30
OK. Several things to look into there, but first things first. Did you check the md5sum of the downloaded ISO?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Did you burn the CD at the lowest speed possible?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

How did you create the bootable USB drive? This for in Windows:

[https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows]("https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows")

**EDIT**: Hah! Rubi1200 beat me to it! Great minds think alike. :)

---

