---
title: "Kubuntu won't boot after update!"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by srdempster on 2008-03-17
I donwloaded Kubuntu DVD from the main site and install, everytime I install it asks to upgrade my distribution upon 1st boot up.The last 3 time's it broke it with an error 15 - file not found on the grub loader screen.
If I preform a normal update (i.e. not distro) then adept crashes half way through and comes up with the same error on reboot!

Help Steve :confused::(:mad:

---

### Post by NightwishFan on 2008-03-17
When you install update through the terminal.
```
sudo apt-get update && sudo apt-get upgrade
```
Post what errors you get.

---

### Post by srdempster on 2008-03-17
error 15 - file not found is what appears every time

---

### Post by NightwishFan on 2008-03-17
I believe you may have to check your repositories. I think there is an option in adept.

---

### Post by srdempster on 2008-03-17
Sorry didn't read properly but I can't as I can't boot into kubuntu at all using safe or normal boot.I'll try the recovery option on the live dvd otherwise it's yet another install!

---

### Post by NightwishFan on 2008-03-17
I am sorry I will start over. I am not really an expert as I am a recent user of Linux. I will however do my best to help as far as my ability goes. Please tell me:

1) What version of Kubuntu is the dvd?
2) What method do you use for the install?
3) Does it work right on first boot if you do not update, (Like can you restart and boot into it fine)

As we go on I will think on this more. I believe a reinstall would be the way to go unless someone else can help more.

---

### Post by srdempster on 2008-03-17
Kubuntu 7.10 gutsy gibbon

It's a clean install on an empty hard drive

It does boot fine every time if no update is performed, this is the 2nd dvd i've downloaded and used.

Steve

---

### Post by NightwishFan on 2008-03-17
When you boot into the system. Do not update but run this command in the terminal and post if anything seems out of the ordinary, (Ordinary is a bunch of links being checked)
```
sudo apt-get update
```

---

### Post by srdempster on 2008-03-17
I gonna have to rescue system first before I can do that or I'll re-download ubuntu on dvd this time save all the sh!t lol!

---

### Post by srdempster on 2008-03-17
couldn't rescue so re-installed and updating via the terminal as you said see what occurs now!:lolflag:

---

### Post by NightwishFan on 2008-03-17
When that finishes if you encounter no errors do:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by srdempster on 2008-03-17
Administrator's it's worth marking this thread or the tips I've been given a a sticky as it's worked better than using apept updater

Steve:KS

---

