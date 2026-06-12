---
title: "Problem installing Ubutu 10.10"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by Jw633morales on 2011-01-12
I used to have a dual boot with Windows Vista, 32bit & Ubuntun 10.04, 32 bit, and it worked well. I recently installed Windows 7, 64bit in my PC, and tried to installed ubuntu 10.10, but for some reason Window 7 stops the ubuntu 10.10 installation.  Can it possibly be a compatibility issue?

---

### Post by shashi859 on 2011-01-12
hi Jw633morales..

normally there will be no comataibilty issues. ubuntu just works with lots of hardware & with co-existing with many other OS..

where actually you get the problem? during which step of installation?
or do u have problem while installation like..unable to load bootloader

---

### Post by Quackers on 2011-01-12
If you have a look in the Windows disk management window you will be able to see how many primary partitions Windows is using. 4 is the maximum (including recovery/data etc).

---

### Post by Jw633morales on 2011-01-12
Thank you for responding so quickly to my message.  It usually stops after two hours in to the installation and the message that displays indicates to check a file in "Windows/c:/program folder / user;alex"(I don't remember well the messages).  And when I look in the program folder I don't find such folder.  I don't know if it is the windows firewall or avast internet security firewall that might be blocking the installation. When I get home I will run installation again and will take print screen of problem so I can posted.  Once again thank you for help.

---

### Post by Quackers on 2011-01-12
Are you installing inside Windows using wubi? I have never used that way myself, but I would be amazed if it should take 2 hours! A normal dual boot installation takes me about half an hour.

---

### Post by bcbc on 2011-01-12
It takes that long because it downloads the Ubuntu CD install image each time you run wubi.exe. If you want to speed it up, download it yourself and place it in the same folder as wubi.exe before running.

The folder containing the log file is identified in the environment variable %temp%. It's a hidden folder. So instead of browsing for it, just enter %temp% in your explorer address bar (or run %temp%). It's called wubi-10.xxx-revnnn.log. If you downloaded it from ubuntu.com's main download site it is actually 10.04.1, not 10.10.

To get 10.10 get your files from [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

Note: you can't install netbook edition or xubuntu using wubi 10.04.1

Heads up: once (if) you get wubi installed, avoid updates to grub (packages grub-pc and grub-common). See the [wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") for what happens.

---

