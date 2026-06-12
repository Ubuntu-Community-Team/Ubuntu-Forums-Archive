---
title: "password not working"
date: 2006-03-06
forum: Installation &amp; Upgrades
---

### Post by edson on 2006-03-06
I wanted to install automatix. Running the command to download it was no problem.
Then using this command to install it:

sudo dpkg -i automatix-ubuntu_5.5-5_i386.deb

you then get asked for the password. But when i try to enter it, the cursormark just blinks, doesn't move, nothing happens. I can't enter the password. 
Anybody knows  why this happens? Do have to have a root password or something?

Also I've downloaded realplayer for linux .bin file to the desktop. 
But when I run this command: chmod +x RealPlayer10GOLD.bin  
i only get something like, file could not be found...
What command should I run to install realplayer?

---

### Post by R3linquish3r on 2006-03-06
#1 The password is not displayed. Just type and the letters will be entered. Its an encryption feature.

#2 You need to "cd" (tell terminal to look in that area) to the place were the file is. For example if it is on your desktop you will type:

```
cd /home/<your username>/Desktop/
```

---

### Post by Lord Illidan on 2006-03-06
[quote=R3linquish3r]

#2 You need to "cd" (tell terminal to look in that area) to the place were the file is. For example if it is on your desktop you will type:

```
cd /home/<your username>/Desktop/
```[/quote]

How about this shorter version:

```
cd ~/Desktop
``` The tilde (~) is a link to your home directory.

---

### Post by edson on 2006-03-06
I'm lost here, maybe i'm missing some steps but when i run these commands
for automatix:

wget [http://beerorkid.com/automatix/automatix_5.5-5_i386.deb](http://beerorkid.com/automatix/automatix_5.5-5_i386.deb)
sudo dpkg -i automatix_5.5-5_i386.deb

and for realplayer linux:

chmod +x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin

still get the same respons, file not found, archive doesn't exist,
where do i put "cd /home/<your username>/Desktop/" ?
I'm not sure what dir automatix is installed in. 
i need more step by step instructions in solving this problem 
since i've never used linux before.

---

