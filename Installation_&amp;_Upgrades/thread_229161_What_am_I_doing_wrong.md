---
title: "What am I doing wrong?"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by SnakeFingers on 2006-08-04
I have a winmodem with a Connexant chipset (HCF). I verified the modem ID prior to Ubuntu install with a utility downloaded from Linuxant. My modem is correctly listed in the installed hardware device list. There is no driver listed though. 

Before installation, I used XP to download linux drivers and documentation for my modem, put them into a folder called Conexant, and burned them to a CD. Then I installed Ubuntu and coppied the files to my home/user directory. I am assuming this method of data transfer does not pose any problems.

I then opened terminal and tried to cd to the conexant folder so I could execute the install instructions, but got an error message saying the file or directory does not exist. 

I can see the files and directory in the graphical file manager. A ls on my home/user folder shows the files and folder too. I can open the documents in the directory by double-clicking on them so I don't think I'm dealing with corrupted data.

Any suggestions? Only have dialup in my neighborhood so this is a show stopper.

---

### Post by 23meg on 2006-08-04
> I then opened terminal and tried to cd to the conexant folder so I could execute the install instructions, but got an error message saying the file or directory does not exist.Please copy and paste the exact command you enter and the error you get. Make sure you're using the correct case; /home/user/Conexant and /home/user/conexant aren't the same directory.

---

### Post by SnakeFingers on 2006-08-04
Not much help 23Meg. I've been cutting and pasting all along. The issue here is that the directory shows up in the file manager and shows up when I run ls on the home/user directory, but is not found when I try to cd into the directory.

This is a default installation, no customization has been done, no permissions changed on anything. This is just plain weird.

---

### Post by Wakker on 2006-08-04
well, I don't know if you figured it out, Linux is CaSe SeNsItIvE;) .

rename the folder "Conexant" to "conexant" (only use lower case)
and then try again and see if it works ^^

---

### Post by SnakeFingers on 2006-08-04
Thanks for the tip Wakker. I am aware that Linux is case sensitive and have taken that into account. I didn't go blindly, but read posts to the forum and the documentation, downloaded drivers, etc. prior to installing. I was ready to go- at least I thought I was. 

I have so far assumed that I've been doing something incorrectly. I'm going to wipe the HD and do a reinstall on the chance that something went awry in my installation.

---

### Post by 23meg on 2006-08-04
In case you misunderstood, what I'm asking you to do is reproduce the situation in a terminal and copy and paste the whole text, including the command you enter and the error you get here. Also please post a link to the install instructions, or if you can't, quote the part that tells you what to do in the terminal.

---

### Post by SnakeFingers on 2006-08-04
23Meg- I did misunderstand what you were asking me to do. I realized what you wanted later this morning. I was a bit frustrated with the whole ordeal. I have 23 years tech experience with computers and operating systems and was beginning to feel like an idiot.

Anyway, the problem is solved. I wiped the drive and did a reinstall and now things work as I expect them to.

Thanks to you and Wakker for your suggestions.

---

