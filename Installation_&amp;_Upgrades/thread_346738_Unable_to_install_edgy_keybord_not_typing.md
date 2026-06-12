---
title: "Unable to install edgy keybord not typing"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by Noiano on 2007-01-26
I paste the ticket posted on [https://launchpad.net/ubuntu/+ticket/3347](https://launchpad.net/ubuntu/+ticket/3347)

[INDENT]

I have been using with allmost no problem ubuntu breezy and dapper. Now I decided to upgrade to edgy to have more update programs. As I heard there were some problem in upgrading i decided for a new clean installation.
So i downloaded the kubuntu iso image, I checked the hash as well as the cd integrity and I tried to install.

Strangely there were lots of problems:
1. Sometimes the live cd didn't start...black screen all the time.
2. When choosing the "start or install" after few seconds the system rebooted.
3. Here's the most strange thing: when, after many reboots, the live session started the keyboard (Logitech access keyboard, PS2) didn't work but the mouse (microsoft intellimouse usb) did work perfectly.

So I was unable to install anything because i could type nothing. Then I tried to select the keyboard layout before choosing "start or install"...nothing. Please note that when the install menu starts the keyboard still works.
After many trials strangely in the end the keyboard worked and I installed the kubuntu edgy. But when I start it by choosing the non recovery mode kernel the keyboard doesn't work so I cannot login to the system and i can only reboot using the mouse.

I also tried to choose the recovery mode kernel and the first time the pc rebooted. The second time it worked and I could access to the root shell. The keyboard worked and I made a apt-update and upgrade...nothing changed.

I have run out of any ideas...i only know i am forced to use windows now....please Help me!

PS: i did the same trials by using the ubuntu edgy cd...always the same problems
[/INDENT]


I am more than desperate (more than housewifes:D )

---

### Post by donatell0 on 2007-02-16
I'h having the same problem dude... I'm downloading the alternate installer and seeing if that will help.. i have a logitech mouse and keybrd and they both dont respond!

---

### Post by Noiano on 2007-02-16
> **donatell0 said:**
> I'h having the same problem dude... I'm downloading the alternate installer and seeing if that will help.. i have a logitech mouse and keybrd and they both dont respond!

have a look here [https://answers.launchpad.net/ubuntu/+ticket/3347](https://answers.launchpad.net/ubuntu/+ticket/3347) I have solved by using the boot command atkbd.set=3..try!

---

