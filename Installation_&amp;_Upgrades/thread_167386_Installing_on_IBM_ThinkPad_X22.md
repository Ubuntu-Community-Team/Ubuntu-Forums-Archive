---
title: "Installing on IBM ThinkPad X22"
date: 2006-04-28
forum: Installation &amp; Upgrades
---

### Post by xxflip on 2006-04-28
_Installing on IBM ThinkPad X22_

My Ubunto install process locks, leaving a blank screen, after I press ENTER at the command prompt and a few setup lines are executed...

Right after it clears the screen and writes "Trying to enable .... buffer ...." it goes blank (it's so fast I can't even read the whole sentence).

Anybody can help out wit this issue?

---

### Post by ssalman on 2006-04-28
I have Ubuntu on a Thinkpad x20. I don't have the docking station, and so I have no CD/FD drives. Instead I used the netboot to get Ubuntu installed through the net. I managed to get Suse 10.0 on it using Netboot too. Damn small linux on there too :).

Post back with your setup (ram, HD, Partitions, Win partition or not), and installation choice (CD,FD,Netboot,...). 

If you don't press enter, where does the process stop, give it 5 minutes to see if it is stuck at some process that for some reason takes a long amount of time.

BTW, did you check the MD5 checksum of the ISO before you burn it (assuming that you are using the CD choice)?

Here is a [link ]("http://www.thinkwiki.org/wiki/ThinkWiki")for Thinkwiki, which I found quite helpful in working with my Thinkpad.

---

### Post by xxflip on 2006-04-28
[QUOTE=ssalman]I have Ubuntu on a Thinkpad x20. I don't have the docking station, and so I have no CD/FD drives.[/QUOTE]
I do have the docking station with mine, thus CD is available.

[QUOTE=ssalman]Post back with your setup (ram, HD, Partitions, Win partition or not), and installation choice (CD,FD,Netboot,...). [/QUOTE]
256 RAM, 20GB HD, PIII 800Mhz, I tried while having a win 2000 partition, and afterwards with no partition. I am trying to install from the CD

[QUOTE=ssalman]If you don't press enter, where does the process stop, give it 5 minutes to see if it is stuck at some process that for some reason takes a long amount of time.[/QUOTE]
I press ENTER at the ROOT: to start the install process. It then executes quite a few lines, but before switching to the graphical interface where it lists the install progress (that's what I think from watching the Live CD boot on another machine) it just stops (disk and CD activity), even after waiting for 3 hours.

I have successfully installed Puppy Linux, and a portuguese distribution of KDE.

Both the Live and Install CD lock at the same position, and I've just downloaded the KUBUNTU ISO and it also lock in the same way.

[QUOTE=ssalman]BTW, did you check the MD5 checksum of the ISO before you burn it (assuming that you are using the CD choice)?[/QUOTE]
the CDs I'm using came through mail from UBUNTU and were used already in other machines.

---

### Post by ssalman on 2006-05-01
[FONT=Verdana][SIZE=2]Hi,
[/SIZE][/FONT]   [FONT=Verdana][SIZE=2]            Over the weekend I tried several times on two laptops to find the message that you have mentioned but with no luck, it looks like it is going too fast for me just before the graphical system goes up. One thing I thought about is instead of pressing enter at the &#8220;Boot:&#8221; prompt, use the vga=xxx option to specify the screen resolution, or try to turn off all dma, apci, and other services that may affect the hardware detection. Look over the F1 through F10 options for more details. I know that is not the answer you were looking for, but that is what I would tinker with if I had this issue. Good luck.[/SIZE][/FONT]

---

### Post by xxflip on 2006-05-02
Thanks for your help. Managed to install ubuntu 5.10 with the following command:

linux vga=771 noapic nolapic

---

