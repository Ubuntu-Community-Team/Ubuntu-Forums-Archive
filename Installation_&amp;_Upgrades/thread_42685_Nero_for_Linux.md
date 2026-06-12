---
title: "Nero for Linux"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by kona0197 on 2005-06-19
I downloaded Nero - it came in a file ending in .deb - how do I install it? Please help!

---

### Post by bored2k on 2005-06-19
[QUOTE=kona0197]I downloaded Nero - it came in a file ending in .deb - how do I install it? Please help![/QUOTE]
 Applications - system - terminal (in your upper panel), then type down:
sudo dpkg -i thenameofthefile.deb

Tip: It is not really good in Linux (I know I know it owns the Windows scene). I suggest you try Gnomebaker or Graveman (wich is my personal favorite :D):
1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. sudo apt-get update
3. sudo apt-get install gnomebaker graveman --force-yes -y

[http://ubuntuguide.org/#gnomebaker](http://ubuntuguide.org/#gnomebaker)

---

### Post by kona0197 on 2005-06-19
OK I now need to enable DMA - how to do that?

---

### Post by bored2k on 2005-06-19
[QUOTE=kona0197]OK I now need to enable DMA - how to do that?[/QUOTE]
 Try the command 
sudo hdparm -d 1 /dev/DEVICENAME (could be /dev/cdrom, /dev/dvd, etc)
[http://www.ubuntuforums.org/showthread.php?t=30949&highlight=enable+dma](http://www.ubuntuforums.org/showthread.php?t=30949&highlight=enable+dma)

BTW, that is really not necessary, unless you persist on using NeroLinux.

---

### Post by kona0197 on 2005-06-19
THANK YOU! You have been VERY helpful!

One last question - how do I get a program like GAIM to start when I boot up Linux?

---

### Post by bored2k on 2005-06-19
[QUOTE=kona0197]THANK YOU! You have been VERY helpful!

One last question - how do I get a program like GAIM to start when I boot up Linux?[/QUOTE]
 Two ways:

A) In your upper panel: System - Preferences - Sessions - Startup Programs - Add - write gaim and press enter.

or

B) Open anything you want to load automatically (Firefox not included), click on log out - save session.

---

### Post by kona0197 on 2005-06-19
By the way - do you know of any themes that will look like XP's luna? The Fisher-Price look? I've looked around but can't find anything!  :|

---

### Post by kona0197 on 2005-06-19
Oh and is there ANY way to make an application quit if it gets frozen?

---

### Post by allforcarrie on 2005-06-19
type Xkill, click the app

---

### Post by drummer on 2005-06-19
[QUOTE=kona0197]By the way - do you know of any themes that will look like XP's luna? The Fisher-Price look? I've looked around but can't find anything!  :|[/QUOTE]
 Perhaps this - [http://art.gnome.org/themes/metacity/501](http://art.gnome.org/themes/metacity/501)
or this - [http://art.gnome.org/themes/metacity/645](http://art.gnome.org/themes/metacity/645)
for more have a look at [art.gnome.org](art.gnome.org) and [www.gnome-look.org](www.gnome-look.org)

---

### Post by lotusleaf on 2005-07-16
I just thought I'd add that I noticed Nero has a trial (demo) version available for their NeroLinux burning program now, for anyone who is interested:

[http://www.nero.com/en/nerolinux-prog.html](http://www.nero.com/en/nerolinux-prog.html)

[color=gray]"NeroLINUX is available for PCs based on a 32-bit x86 architecture.

You can download NeroLINUX for the following packet manager:
deb 	- Debian packet manager
rpm 	- Red Hat packet manager"[/color]

Just for the hell of it I installed it but I haven't tested it yet.

---

### Post by pt123 on 2005-07-16
Can you enter your windows version serial ?

---

