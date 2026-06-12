---
title: "Installing Kubuntu from CD problems"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by fizgig on 2005-03-15
I just tried a fresh install of Kubuntu from the regular 5.04 CD (not live).  Got to the point where I have to reboot and GRUB loads linux fine.  Trouble is, I go to a shell - X isn't started.

I tried "kdm","gdm","startx" and all returned not found.

I don't even have an /etc/X11 dir!  Did I do something wrong?  Should I try the liveCD instead?  Any drawbacks to using the liveCD?

---

### Post by aj2010 on 2005-03-15
Hi,

unfortunately the current Kubuntu CD missed to install the remaining packages therefore in the current state you have only the base install.
Please enter in the konsole "sudo apt-get install kubuntu-desktop" with inserted CD.
Hope this helps!

---

### Post by fizgig on 2005-03-15
Well, sudo su or su wont let me into root mode.  Says it's missing some authorization stuff  :?

---

### Post by aj2010 on 2005-03-15
No, use sudo and enter your user password...

---

### Post by fizgig on 2005-03-15
[QUOTE=aj2010]No, use sudo and enter your user password...[/QUOTE]

Sorry, I tried that first  but forgot to mention that 8) 

Unfortunately, that didn't work either.  I might have been root when I was first dumped to a prompt but I can't touch root priviledges now.  Would it be better to install regular hoary and then add the kubuntu packages later?  I'd like to save space and not install the GNOME desktop if I don't have to since I plan to use KDE completely.

---

### Post by aj2010 on 2005-03-15
when you dumped to the prompt then login as user afterwards enter sudo apt-get install kubuntu-desktop ...
It definitely works I had the same problem some days ago.

---

### Post by fizgig on 2005-03-15
[QUOTE=aj2010]when you dumped to the prompt then login as user afterwards enter sudo apt-get install kubuntu-desktop ...
It definitely works I had the same problem some days ago.[/QUOTE]

Well, here's what I get when I type "sudo apt-get install kubuntu-desktop" without quotes:

[B]sudo: unable to lookup sexylaptop via gethostbyname()
Password:postdrop: warning: unable to look up public/pickup: No such file or directory[/B]

it stays like that and doesn't even give me the next prompt until I hit ctrl-c

ps. "sexylaptop" is the name of my computer

---

### Post by fizgig on 2005-03-16
man, I'd sure like to install kubuntu.  Can anyone help me out?

---

