---
title: "Upgrading from Ubuntu 12.04 to 14.04"
date: 2016-04-01
forum: Installation &amp; Upgrades
---

### Post by acefromspace on 2016-04-01
I have never done an upgrade... always just do fresh install. Any specific issues with upgrade from 12.04 to 14.04? I will back up all data first.

---

### Post by grahammechanical on 2016-04-01
Disable any PPAs. Change the video driver to the open source video driver, Revert the desktop to as default as possible. Read the release notes.

Regards.

---

### Post by acefromspace on 2016-04-04
Thank you. I am almost done backing up data. I will try this (mostly out of curiosity), but will end up doing fresh install later. I know how to save my browser bookmarks, but is there a simple way to save a list of the software programs I added after install? Basically, what shows on the unity launch menu (I miss command line... getting spoiled) I have really enjoyed Ubuntu 12.04 and have almost no issues. Years ago, I would mention Linux and people didn't get it, but times have changed and they are catching on... Linux has come a long way. I started with Fedora, but someone showed me Ubuntu and I've never looked back. By the way, I did read the release notes on 14.04 and it look similar to 12.04 (that's fine with me)
I have an Ubuntu install file (ubcd533.iso) is that 14.04? Before I burn it to disc, want to be sure it's not my old 12.04 (running out of DVDs from all the data backups and want to do this soon)

---

### Post by RobGoss on 2016-04-05
> **acefromspace said:**
> Thank you. I am almost done backing up data. I will try this (mostly out of curiosity), but will end up doing fresh install later. I know how to save my browser bookmarks, but is there a simple way to save a list of the software programs I added after install? Basically, what shows on the unity launch menu (I miss command line... getting spoiled) I have really enjoyed Ubuntu 12.04 and have almost no issues. Years ago, I would mention Linux and people didn't get it, but times have changed and they are catching on... Linux has come a long way. I started with Fedora, but someone showed me Ubuntu and I've never looked back. By the way, I did read the release notes on 14.04 and it look similar to 12.04 (that's fine with me)
I have an Ubuntu install file (ubcd533.iso) is that 14.04? Before I burn it to disc, want to be sure it's not my old 12.04 (running out of DVDs from all the data backups and want to do this soon)

Not really sure how to save a list for favorite software that's installed it might be easier just to right down your favorites on paper. I use the same software so it's kind of easy for me to remember when I do new installations.

---

### Post by howefield on 2016-04-05
> **acefromspace said:**
> ...but is there a simple way to save a list of the software programs I added after install?

You could use Synaptic Package Manager to generate a package download script, or do it from the command line with dpkg, alternatively the Software Centre has a package syncing option but I am not sure how well this works. Possibly well enough.

> I have an Ubuntu install file (ubcd533.iso) is that 14.04? Before I burn it to disc, want to be sure it's not my old 12.04 (running out of DVDs from all the data backups and want to do this soon)

Looks like it could be an .iso file for the Ultimate Boot CD.

---

### Post by Bucky Ball on 2016-04-05
[From here]("http://www.ubuntu.com/download/desktop") is best for the ISO. 

If you're going to do a clean install later anyway, make it 16.04 LTS, the next LTS, due in about three weeks. ;)

---

### Post by acefromspace on 2016-04-05
Woops! It is Ultimate Boot disc. Thanks for the tips... I will try dpkg in command line (is that all I type, or should I add something?)

---

### Post by howefield on 2016-04-05
> **acefromspace said:**
> Woops! It is Ultimate Boot disc. Thanks for the tips... I will try dpkg in command line (is that all I type, or should I add something?)

Something that has worked for me is to generate the package list with..

```
dpkg --get-selections | grep -v deinstall > ~/Documents/packages
```

and this to restore from the package list on the new install.

```
sudo bash -c "dpkg --merge-avail <(apt-cache dumpavail)"
sudo dpkg --clear-selections
sudo dpkg --set-selections < ~/Documents/packages
sudo apt-get dselect-upgrade
```

Although these days a simple text file with all the steps that I do to a new install suffices, and includes a sudo apt install "*listofpackages*" line, eg sudo apt install keepass gimp flac ect ect ect..

---

### Post by acefromspace on 2016-04-06
I ended up just making a list in text editor... actually the easiest way after all.
I'm glad it was time to do this because it forced me to back-up all my data (haven't done this in a long time)

---

### Post by acefromspace on 2016-04-17
I'm ready... all data backed up, ubuntu 14.04 downloaded and burned to dvd (just in case), saved bookmarks, list of packages, ect. The truth is, at this point I would have just done fresh install, but I am curious. My system is very basic out of the box... nothing fancy, and video card shows no specific driver (I've used 3rd party driver before with no problems, but don't think I bothered this time) Countdown... 10, 9,8,7,6... upgrading.

---

### Post by acefromspace on 2016-04-17
OK, everything is working fine, but 366 Kb... I can do fresh install and most packages in the same time. Didn't know it would take that long. Doing fresh install in the morning. Thank you for the advice... might help anyway.

---

### Post by Bucky Ball on 2016-04-17
A fresh install of 14.04 LTS or 16.04 LTS? 16.04 LTS is about 48 hours from being officially released. :)

---

### Post by howefield on 2016-04-18
> **acefromspace said:**
> OK, everything is working fine, but 366 Kb... I can do fresh install and most packages in the same time. Didn't know it would take that long. Doing fresh install in the morning. Thank you for the advice... might help anyway.

One of the (many) reasons I prefer fresh installs is that the time it takes is not much different to an upgrade, and often much less. To install, configure and image the drive takes me around 45 minutes and you still have the installation .iso for future use.

---

### Post by acefromspace on 2016-04-19
Did fresh install of ubuntu 14.04 (no hurry... will try 16.04 soon) After install (and updates) did the restricted extras and (as usual) walked away and forgot the ms fonts eula, so fixed that today. All is well. All my software installed. Got a bit worried when my screen kept dimming, but remembered I hadn't done settings yet, so did my usual settings for system and firefox browser. At this point, I don't see why people bother with upgrades. Also, I usually install system, then do update later (I was told it isn't any faster to do both at same time when installing) but I was surprised it did seem faster overall (doing both)

---

### Post by RobGoss on 2016-04-20
You'll have **16.04** in a few hours I would just wait it might same any problems you might encounter

---

