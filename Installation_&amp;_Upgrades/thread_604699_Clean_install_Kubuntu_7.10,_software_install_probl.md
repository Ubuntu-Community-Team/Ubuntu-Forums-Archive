---
title: "Clean install Kubuntu 7.10, software install problems"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by Bart Ellebaut on 2007-11-06
After a lot of troubles I finaly got Kubuntu 7.10 installed on my Toshiba Satellite.

First I had the black splash screen problem. Fixed that.
Then I saw the splash screen but no login screen. Fixed that.

Now I'm in Gutsy Gibbon and wanted to run Firefox. Seems it is not in my Internet applications list. So I opened Adept Installer. I see Firefox in the list, but it's grey and I can't check the box to make clear I want to install it...
Same fot Thunderbird, the Gimp etc...

What is going wrong here?


Another question. The installation happened in Dutch as I selected that language in the early stage of the install. Now Kubuntu is in English and when I go to the System Settings - Regional & Language trying to install a new language, onlu English is in the list... how come?

---

### Post by bulldog on 2007-11-06
Did you upgrade or did you a clean install?

Ik heb het ook in het Nederlands geinstalleerd [verse installatie] en geen problemen mee gehad,wel op een desktop in plaats van een laptop.

---

### Post by Bart Ellebaut on 2007-11-06
Clean install, on a second partition.

Problems I had were the black screen instead of splash screen (edited the usplash.conf to 1024x768 ) and login screen (edited driver in xserver-xorg).

Strange huh! Also, the menu bar was at the top when using live cd, after install on partition it's on the bottom and the shutdownbutton is gone on the right.

---

### Post by bulldog on 2007-11-06
Do you have a separate /home by any change?
And if so,did you use the same name and password in Gutsy?

My mistake,you're using Kubuntu,by my knowing the KDE panel is at the bottom isn't it?

---

### Post by Bart Ellebaut on 2007-11-06
What do you mean by separate /home?

On partition one is 6.06 LST
On partition two is 7.10

No, different user and password.


Indeed at the bottom, but if my memory serves me right, when booting from the live cd it was at the top (or I'm confusing with 6.06 Gnome I used earlier today)

---

### Post by bulldog on 2007-11-06
Separate /home is another partition for your user folders.
I always use 10Gb for a distro's /root partition and I have a huge /home for the personal stuff.
When doing a fresh install mount your /home as /home and choose another login name so there can't be any mixing with config files.
this way you can keep all your personal data when you do a fresh install or even if you install a number of distro's at the same time.

---

### Post by Bart Ellebaut on 2007-11-06
Aha, good to know, but that still doesn't solve my 2 initial problems :)

Or should I start all over again and when installing Kubuntu 7.10 I immediatly delete the partition from 6.06. So a real totally clean install?

---

### Post by bulldog on 2007-11-06
The Dapper partition has nothing to do with your Gutsy,they are two different partitions :)
But reinstalling Gutsy is half an hour work so it should be quicker as waiting on an answer here.
Check the cd on errors before you install anyway.

---

### Post by Bart Ellebaut on 2007-11-06
Install worked, all in Dutch now, and Firefox and stuff are clickable in the Adept installer. Only when I choose update and it tries to send the headers or something (I'm a linux n00b) it give's an error.

---

### Post by Bart Ellebaut on 2007-11-06
All works fine after a simpel reboot :)

---

### Post by bulldog on 2007-11-06
Nice to hear....sometimes  this is  the fastest way to get it up and running again :guitar:

---

