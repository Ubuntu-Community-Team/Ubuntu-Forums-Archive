---
title: "Release Upgrade 14.01.1 &gt; 16.04.1"
date: 2016-07-27
forum: Installation &amp; Upgrades
---

### Post by mikodo on 2016-07-27
First time ever. It went fine. I just did it to try the release upgrade.

Only thing I didn't know what to do was, to get out of a window asking me if I wanted to upgrade a library, stay on the same, check it out and a couple of other options. I hit the command to look to see what it was, (something I no longer use), but couldn't find the key-press to exit the window and continue. Went in to a tty and received a message to continue dpkg ... and hit yes and off it went again until it finished.

Booted into my already installed 16.04.1 and re-installed grub and updated it to give it control of grub again. 

If I were to keep the upgrade, all I would have to do is customize the desktop. Everything I tried, seems to be working with it. 

A smooth experience.

Thanks.

---

### Post by grahammechanical on 2016-07-27
I think that those kind of dialogs are text box and not GUI. So, tab will move through the options.

Regards.

---

### Post by alan-pd-watson on 2016-07-27
mikodo - did you upgrade by software updater or though some other process?

---

### Post by mikodo on 2016-07-27
Hello.

> **grahammechanical said:**
> I think that those kind of dialogs are text box and not GUI. So, tab will move through the options.

Regards.

Yes, I expect it is something like that I couldn't figure out. I chose the option by tabbing I believe to, see a further explanation. It was the library for a old printer I no longer have. With that information displayed I didn't see how to leave that page to go on with the upgrade. I became impatient as, I had scheduled the upgrade process while I needed to do other things at home. I would come into the office to see how it was doing and found it asking questions from time to time and then once answered it would continue. So, in fairness, I found a way in a tty that worked well and left it at that. 

> **alan-pd-watson said:**
> mikodo - did you upgrade by software updater or though some other process?

Important question.

I didn't know how I wanted or how it would be best to do it. So, I explored a bit.

My first thoughts were to use < sudo aptitude safe-upgrade && sudo aptitude full-upgrade >. I used to use < sudo aptitude safe-upgrade > when upgrading my installs.  It and apt are both front ends for dpkg. In my time dual-booting with Debian I used Aptitude for both Ubuntu && Debian. In Debian at that time it was often stated to be a superior way. I also had read that one shouldn't mix and match usage of the two together. If that is still a consideration I can't comment on nor, if that was actually true. Just what I had read in a couple of instances.

If I may, I'll suggest you read the excellent explanation by T.J. of the comparisons of apt && aptitude written in a thread that was a multi-version upgrade in post #8 [https://ubuntuforums.org/showthread.php?t=2330226](https://ubuntuforums.org/showthread.php?t=2330226)

> I would install aptitude, and use the command:

*aptitude full-upgrade*

Aptitude has better resolution logic than standard apt when selecting  install order.  Aptitude and apt-get do the same things - that is true,  but they vary in subtle ways that are important.  In almost all cases,  aptitude selects and orders upgrades in a more conservative manner than  apt-get that should lead to a more successful upgrade between two  versions that are so disparate. Most people use apt-get because it is  usually easier to remember.  Still, I do not understand why aptitude is  not standard on Ubuntu.


Then, I thought of letting the software updater do it, but it in the end I decided to stay with cli and upgrade my Xubuntu _Desktop_ install with:

```
sudo do-release-upgrade

```
If, I remember correctly, it told me that 16.04 was available and in the end, now that 16.04.1 is out, it upgraded from 14.04.1 > 16.04.1.

See this page that influenced my final decision: [https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)


[URL="https://ubuntuforums.org/showthread.php?t=2330226"]
[/URL]

---

