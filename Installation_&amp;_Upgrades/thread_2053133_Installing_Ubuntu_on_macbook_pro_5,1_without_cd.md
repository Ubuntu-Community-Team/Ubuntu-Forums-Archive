---
title: "Installing Ubuntu on macbook pro 5,1 without cd"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by Tartakower on 2012-09-04
Hello people!

(if you don't want to read my whole life -> just jump to the "my questions" section)

First post on this forum as I'm just starting my journey into the linux world ^^
Right now, I'm running Mac OS X 10.6.8, I'm studying computer science and enjoys programming&developping for myself. The problem being that I'm often getting stuck by some limitations of OS X, which is not aimed at developpers/power users.

So, time to switch to linux!
I want to take Ubuntu as first as I want something that runs smooth and is easy to use, I'll maybe look for a more power-user oriented distribution later. After having done the regular back-ups, I started trying to install ubuntu last week.

My biggest problem is that my macbook pro is getting pretty old (4 years in november) and the cd/dvd-reader is dead.

I've already installed refit and gdisk ([http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)) to be able to mess a little bit more freely with the partitioning and the startups.

I tried to install ubuntu from a USB stick and that's where it starts to be tricky:
- I used dd to copy the ubuntu-12.04.1-desktop-amd64+mac disk image to a usb stick as explained by this tutorial: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx) and tried the standard procedure to install, but the computer doesn't detect the usb-stick on startup when pressing the alt/c key
- I then found this tutorial: [https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick) which tells me to resync my partition tables with refit, which I don't know how to do.

So, **my questions are:**
- Anyone succeeded in installing ubuntu on a macbook pro with a usb? How?
- How can I resync my partition tables with refit? (I didn't find anything conclusive about this on the internet for now...)
- If I want to create a separate bootable linux partition directly on my HD (as suggested for the macbook air 3,2 in the last tutorial), what's the filesystem I should use for that partition?

Thanks for your answers!

---

