---
title: "Upgrade to 15.04"
date: 2015-07-15
forum: Installation &amp; Upgrades
---

### Post by Lewjay on 2015-07-15
I have been using the 14.xx release for a long time and finally decided to upgrade.  Got the 15.04 tor_rent to download using Deluge.   I can see the file in the File drawer but cannot get it to install.  Have no idea what I'm doing and now this thing is underlining what I type.  _If I double click on icon for 15.04 it wants to save it to a disk but the HD is not an option.

---

### Post by dino99 on 2015-07-16
in order to upgrade Ubuntu to a newer release you have to run in terminal

> sudo do-release-upgrade
that is, delete your deluge download, and check the links below if you want/need to learn about ubuntu.

---

### Post by Bucky Ball on 2015-07-16
You are looking to clean install or a net upgrade? If the former, you have downloaded the .iso file. Now you need to burn a disk image to either USB or disk and boot from it to install. If you need help with that, just ask.

If the latter, you can do as dino99 suggests (you will need 'sudo' before that command') or head for 'Software and Updates'> Update tab and make sure you are being notified of ALL available releases and not just LTS ones. You will then be asked to update and should be offered 15.04 upgrade. You will need to be online with an ethernet cable to do this (more reliable as if wireless snaps halfway through an upgrade you can be in a world of pain). 

I will say that unless you have a specific reason and don't mind upgrading every six months, why are you upgrading a completely functional and stable LTS OS that is supported until 2019? Just curious. 15.04 is supported until January 2016, in case you were unaware of that, at which time you will need to upgrade to 15.10 which has nine months support from October this year and then to 16.04 LTS, which is supported for five years for April 2016.

Good luck however you swing. :)

---

### Post by coffeecat on 2015-07-16
> **Lewjay said:**
> Have no idea what I'm doing and now this thing is underlining what I type.

You must have accidentally clicked the _[FONT=System]U[/FONT]_ button in the message editor toolbar and enclosed a part of your text between [noparse]_ and _[/noparse] BBCode tags. If you have any questions about using the forum, including the editor toolbar and/or BBCode, you are very welcome to start a thread in the [Forum Feedback & Help]("http://ubuntuforums.org/forumdisplay.php?f=48") section.

---

### Post by grahammechanical on 2015-07-16
Stick with 14.04 until the end of April 2016 then you can directly upgrade from 14.04 to 16.04. If you install 15.04 you will have to upgrade to 15.10 by the end of next January.

Is there something wrong with 14.04? Upgrading a broken OS does not usually fix the problems. A fresh install might. The torrent application downloads the Ubuntu ISO image. We then have to burn it to disk/USB stick to install Ubuntu from it.

To upgrade an existing OS while using it we use the Update Manager. Run the command suggested by Dino99 but remember, first you will upgrade to 14.10 and then you will have to do it all again to get to 15.04. And 14.10 reaches end of life the 23rd of July 2015. Then upgrading gets much more complicated.

Regards

---

### Post by Bucky Ball on 2015-07-16
> **grahammechanical said:**
> Stick with 14.04 until the end of April 2016 then you can directly upgrade from 14.04 to 16.04. If you install 15.04 you will have to upgrade to 15.10 by the end of next January.

Is there something wrong with 14.04? Upgrading a broken OS does not usually fix the problems. A fresh install might. The torrent application downloads the Ubuntu ISO image. We then have to burn it to disk/USB stick to install Ubuntu from it.

To upgrade an existing OS while using it we use the Update Manager. Run the command suggested by Dino99 but remember, first you will upgrade to 14.10 and then you will have to do it all again to get to 15.04. And 14.10 reaches end of life the 23rd of July 2015. Then upgrading gets much more complicated.

Regards

Pretty much exactly what I said in post #3 (apart from the bit about upgrading not fixing a broken system which is a good point). :)

---

### Post by Lewjay on 2015-07-16
Thanks for the Info.  Did not realize that 15.04 was just a short time support thing.  Guess I'll just stick with 14. xx for now.  Appreciate the help

---

### Post by Bucky Ball on 2015-07-16
All good. Please mark the thread as solved (see second link in my signature).

Incidentally, LTS upgrades to LTS. In other words, when 16.04 LTS is released you will be able to upgrade 14.04 LTS> 16.04 LTS via the net without needing to upgrade through the interim releases. 

In other words, to get to 16.04 LTS from 15.04 you would need to either clean install or upgrade via the net 15.04> 15.10> 16.04 LTS. If you open 'Software and Update' and 'Updates' tab you can set it to only notify you of LTS releases. 

Good luck with it all and post a new thread for any other questions/support requests. :)

---

