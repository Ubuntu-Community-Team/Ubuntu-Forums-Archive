---
title: "I can't install ubuntu 7.10 desktop"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by new11 on 2008-04-10
Hi
I installed ubuntu 7.10 server on my dell laptop with no problems.
now i want to change it or install ubuntu 7.10 desktop.
booting from cd give me a option list intall/run ubuntu...and so on I choose install the cd start for few minutes than an error messages appear: I/O error error reading boot cd reboot. so i reboot and again and agin and again.

I need help please to install it pls

---

### Post by Fire_Chief on 2008-04-10
You don't have to reinstall to get the desktop environment. You just need to install it from the existing Ubuntu Server system that is already running.```
sudo apt-get install ubuntu-desktop
``` This will install the Gnome desktop for you. If you want to try another desktop environment (KDE, XFCE), just replace ubuntu-desktop with kubuntu-desktop or xubuntu-desktop.

Cheers!

---

### Post by warp99 on 2008-04-10
> **Fire_Chief said:**
> You don't have to reinstall to get the desktop environment. You just need to install it from the existing Ubuntu Server system that is already running.```
sudo apt-get install ubuntu-desktop
```

You also need to install the desktop kernel instead of the server kernel in order to install drivers for certain mice and other desktop stuff. So your string would look like this:

```
sudo apt-get install ubuntu-desktop linux-image-2.6.22-14-generic
```

You can run server applications on a desktop kernel without any problems.

Edit:
If you need to boot to a login screen install the gdm package along with the other packages otherwise you'll boot to a prompt and will need to login then enter 'startx' to run the desktop.

---

### Post by new11 on 2008-04-10
Thanks for the very fast reply...

I tried the 2 commands with server cd, descktop cd, even without a cd.
I kept getting the same message:

reading package lists...done
building dependecy tree
reading state information...done
E: couldn't find package ubunt-desktop

waiting for your reply
thanks in advance

---

### Post by new11 on 2008-04-10
when you type a long command what do you type to continue on the next line?
thanks

---

### Post by oldos2er on 2008-04-10
The package name is ubuntu-desktop, not ubunt-desktop.

 If you have a long command, just keep typing; the text will automatically wrap. Then press 'Enter' when you're done.

---

### Post by jaws31415 on 2008-04-10
I'm having this same problem. does anybody now how to get around this?

---

### Post by Moejoe1 on 2008-04-10
Im not getting the exact same error message but I cant get the desktop to load like you too. I have been here all day lost!!! I cant get past this  dos-like screen. My server doesnt go on the net so if it needs to to go forward, im in trouble!

---

### Post by new11 on 2008-04-10
thanks for everyone.
-the syntacs error was only in my message on the forum.
-any way still not working, i'm still waiting or a solution if somebody can help please don't hezitate...

thanks again

---

### Post by bradwilliamson on 2008-04-10
Have you enabled the internet repositories? It sounds like you may only be seeing the packages available on the original CD you installed with.

run:

sudo nano /etc/apt/sources.list

And make sure that it looks something like this:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

You can have them all on one line too:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse

Save it
Then run:
sudo apt-get update

Then see if the ubuntu-desktop is listed in the repositories with:
apt-cache search ubuntu-desktop

and you should get something like this:

brad@shark:~$ apt-cache search ubuntu-desktop
edubuntu-desktop - edubuntu desktop system
edubuntu-desktop-kde - edubuntu desktop system with KDE desktop
kubuntu-desktop - Kubuntu desktop system
ubuntu-desktop - The Ubuntu desktop system
xubuntu-desktop - Xubuntu desktop system

If you don't get them listed here, the *sudo apt-get install ubuntu-desktop *won't get you very far.

Hope that helps
Brad

---

### Post by warp99 on 2008-04-10
The server is not auto-mounting the drive you need to mount the CD-Rom before it can get the packages. This guide will help you on mounting file systems:

[https://help.ubuntu.com/community/Mount?highlight=%28mount%29%7C%28cdrom%29](https://help.ubuntu.com/community/Mount?highlight=%28mount%29%7C%28cdrom%29)

---

