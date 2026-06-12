---
title: "Trouble Partitioning when installing Ubuntu feisty"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by Jimiodom on 2007-07-05
Greetings.

I am switching OS from Windows Vista: Home Basic, to Feisty. i put in the ubuntu disc, and start the installation, but when it starts to partition, i get this error message:

"The creation of swap space in partition #5 of SCSI1 (0,0,0) (sda) failed.:".

I went to the release notes ([here]("http://www.ubuntu.com/getubuntu/releasenotes/704")) and tried to fix it using the fix for Bug #107259, but I cant find "settings" under my "applications".

Would anyone be able to help me out? This is my first time using anything other than windows, so gimme a break :).

---

### Post by coherent.noise on 2007-07-05
I was having the same problem. As a matter of fact, I was searching right now to solve it. Anyway, I suppose your problem, if it was like mine, was that there is no clear way to go to "Applications -> Settings -> Settings Manager" since there is no "start menu." So, I right clicked on the desktop and chose the last option (something about settings, if I recall -- I don't want to mess with it now since it's installing). Anyway, from there you can choose the way that it responds to a right click. I checked a box there, hopefully it's clear when you get there, and accepted the changes. From there you can right click on the desktop to go to settings. Everything now is like the [link]("http://www.ubuntu.com/getubuntu/releasenotes/704") you gave.

Sorry if that was at all unclear. Hopefully you can sort it out. If not, just ask me to clarify and I will go through it again paying more attention. I'm installing right now, but I wanted to respond as soon as I knew it worked.

---

### Post by Jimiodom on 2007-07-05
I right clicked on the desktop like you said, but i see nothing along the lines of settings.

"create folder
create launcher...
create document       >
------------------------------------
Clean up by name
keep aligned
------------------------------------
paste
------------------------------------
change desktop background"

thats what comes up when i right click on the desktop on the boot up feisty desktop.

---

### Post by coherent.noise on 2007-07-05
OK, sorry I didn't keep note better as I was going through it. I will rerun the installer as soon as it's done and take note of what it says.

---

### Post by Jimiodom on 2007-07-05
is there any way i can just wipe my hard drive, then install Ubuntu after that? Right now, even if I take the Ubuntu CD out of my drive, it wont let me boot my computer back to Vista. it has boot problems now.

---

### Post by coherent.noise on 2007-07-05
By the way, I'm working with Xubuntu. That's probably why your right click menu was different. (Mine has "Desktop Settings" as the last option.) I assumed it was Xubuntu because the bug fix you mentioned was for Xubuntu.

Anyway, I'm not really any more experienced than you. So if that didn't help, I don't really know what to say. Hopefully someone that knows what's going on can help.

---

### Post by Jimiodom on 2007-07-05
ohh haha no wonder it didnt look familiar at all haha. ok thanks man.

---

### Post by coherent.noise on 2007-07-06
I suppose I should thank you because your post for help is what directed me to get my Xubuntu install up and running!

---

### Post by Pumalite on 2007-07-06
Use Gparted to prepare and partition your drive. Then install.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

