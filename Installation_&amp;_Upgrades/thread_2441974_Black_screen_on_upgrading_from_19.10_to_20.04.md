---
title: "Black screen on upgrading from 19.10 to 20.04"
date: 2020-04-28
forum: Installation &amp; Upgrades
---

### Post by mustafaemad on 2020-04-28
Upgrading from Ubuntu 19.10 to Ubuntu 20.04 gave me black screen while upgrading what should I do?

---

### Post by ajgreeny on 2020-04-28
What you must do to help us help you is tell us a lot more about your hardware and which particular version of 20.04 you have installed otherwise we will all be "shooting in the dark".

Show us the ouitput in terminal of ***inxi -Fzx*** (from a live system if necessary.)

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by mustafaemad on 2020-04-28
Upgrading from updater my hardware Gigabyte h61 4 G ram

---

### Post by ajgreeny on 2020-04-28
> **mustafaemad said:**
> Upgrading from updater my hardware Gigabyte h61 4 G ram
Sorry but that does not help at all.  I was hoping to see something about your graphics card, perhaps that you have an nvidia card which needs boot option ***[nomodeset]("https://help.ubuntu.com/community/BootOptions")***

After booting to your black screen use Ctrl+Alt+F2 to get to a tty command line.  Login with your username and password, you will see no password when you type, not even asterisks so type carefully.

Then run ***inxi -Fxz > hardware.txt*** which will save the output as a file called hardware.txt.  Hopefully you will be able to either retrieve that file with a live system and let us see it.

---

### Post by mustafaemad on 2020-04-28
The problem was solved with manual reboot only

---

### Post by zombii2 on 2020-05-12
I had the same problem exactly and it seemed indeed to be installed and working after manual reboot. However I'm not sure everything has gone right during the update because it just went black and I never was told the system has been updated.

---

