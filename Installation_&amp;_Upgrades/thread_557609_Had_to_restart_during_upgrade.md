---
title: "Had to restart during upgrade"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by MCBTunes on 2007-09-22
I had to restart my computer during an upgrade from 6.10 to 7.04(which i did through the update manager). Upon going back to my upgrade manager it only did 2 more minutes of upgrades and it seems like nothing has changed really. Except for now when I boot in and when I go online it says kubuntu instead of ubuntu which is weird.

Is there any GUI difference between 6.10/7.04? Or is there anyway I can check to be sure everything was completed properly?

---

### Post by Pumalite on 2007-09-22
At the terminal:

uname -r

---

### Post by MCBTunes on 2007-09-22
2.6.20-16-generic

is the output when i type that

---

### Post by Pumalite on 2007-09-22
Is that the same kernel you had before or is it new?
You can also see it Grub. Usually an upgrade gives you a new kernel, but leaves the old one in the Grub menu.

---

### Post by MCBTunes on 2007-09-22
I just rebooted and there are 2 different sets of numbers,

there are two of the above mentioned (the top two) and about 6 of a number 2.6.17-12.... does this mean the entire installation is done? Keep in mind I'm not certain if it was like that before or not.

I should be able to feel some sort of difference shouldnt I?

---

### Post by Pumalite on 2007-09-22
If you have a working system stay put.
Lets try this:

sudo apt-get update

Post the output.

---

### Post by MCBTunes on 2007-09-22
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release.gpg [191B]                
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Translation-en_US
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/universe Translation-en_US
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Fetched 3B in 4s (1B/s)
Reading package lists... Done
michael@michael-linux:~$

---

### Post by Pumalite on 2007-09-22
Looks OK to me. I you later on run into problems; post back. Good luck.

---

### Post by MCBTunes on 2007-09-22
ok, thanks.

---

### Post by Pumalite on 2007-09-22
You are welcome.

---

