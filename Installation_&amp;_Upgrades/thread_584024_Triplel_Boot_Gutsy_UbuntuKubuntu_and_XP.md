---
title: "Triplel Boot Gutsy Ubuntu/Kubuntu and XP"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Dougie on 2007-10-20
I want to boot Ubuntu (Gutsy) and Kubuntu (Gutsy) and XP.

(I know I could use both KDE and Gnome from Ubuntu but want a test partition with Kubuntu in it).

I installed Ubuntu - worked fine, got Compiz working - very impressed, lovely work 7.10 !

I then installed Kubuntu - worked fine too. But my Ubuntu wouldnt start properly - blank screen though my wireless light was on. Used recovery console to uninstall XGL as I thought it was my xserver but to no avail. Went through all the log files but saw nothing to say what the problem was. 

I run grub in a seperate partition so I changed menu.lst for both these systems to see if that made any difference. No it didnt. Kubuntu started but still the blank screen for Ubuntu.
So I did a re-install of Ubuntu - worked just fine. But now Kubuntu gets the blank screen !

I share a swap file and run a Dell 9400.

Have I missed something (probably obvious ?)

Dougie

---

### Post by todir on 2007-10-20
Why do you need to install ubuntu&kubuntu :confused: Pick one of them ;) Then just install KDE or gnome desktop.
"sudo apt-get install kubuntu-desktop(or ubuntu-desktop)" :)

---

### Post by Dougie on 2007-10-21
Thanks for this but it should work and in future I would want to try out an install on my test partition before moving it to the main one and there seems to be problem with this. I wonder if anyone else has come across it ?

---

### Post by davidjmayo on 2007-10-21
I had this problem when I was testing Gutsy but wanted to keep my Feisty (both kubuntu but that shouldn't make a difference)

When I used separate swap partitions for each (which in theory you shouldn't have to do) it was no problem

It's worth a shot to see if the same happens for you but no guarantee!!

---

### Post by jennymanda on 2007-10-21
See this

[http://ubuntuforums.org/showthread.php?t=584706](http://ubuntuforums.org/showthread.php?t=584706)

Mine works now!

---

### Post by Dougie on 2007-10-21
Thanks for all the help.

When I edited the fstab file with the correct uuid it worked just fine.

Dougie

---

### Post by jennymanda on 2007-10-21
I think we both learned something today...

---

