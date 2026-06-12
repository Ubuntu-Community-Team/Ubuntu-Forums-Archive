---
title: "Two Ubuntu Versions Reported in One Installation"
date: 2012-09-16
forum: Installation &amp; Upgrades
---

### Post by Wilburight on 2012-09-16
Since I prefer the pre-Unity look and feel, I've been using an older Ubuntu on my desktop PC and as time went by I'd forgotten exactly which version it was. On checking today for a Firefox update, I've found my Ubuntu is reported as being v10.10 and v11.04 depending on whether I click through menus System/Administration/System Monitor or System/About Ubuntu respectively.

FWIW, I've been happily dual booting Ubuntu (as my primary OS) and Windows for years and can't recall ever doing a re-install of Ubuntu - just updates. Also although I'm a long time Ubuntu user and occasional tinkerer if it's something simple, I'm far from Linux fluent.

Can anyone suggest what's going on and how to remedy the ambiguity?

---

### Post by oldfred on 2012-09-16
What does terminal say:

 uname -a

 lsb_release -d

 cat /etc/issue

 gnome-shell --version

 echo $DESKTOP_SESSION

---

### Post by Wilburight on 2012-09-17
Terminal response -

```
festus@Festus:~$ uname -a
Linux Festus 2.6.35-32-generic #68-Ubuntu SMP Tue Mar 27 17:01:54 UTC 2012 i686 GNU/Linux
festus@Festus:~$ 
festus@Festus:~$ lsb_release -d
Description:	Ubuntu 10.10
festus@Festus:~$ 
festus@Festus:~$ cat /etc/issue
Ubuntu 10.10 \n \l

festus@Festus:~$ 
festus@Festus:~$ gnome-shell --version
The program 'gnome-shell' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-shell
festus@Festus:~$ 
festus@Festus:~$ echo $DESKTOP_SESSION
gnome
```

Hope this helps - thanks for your interest! ;)

---

### Post by oldfred on 2012-09-17
The kernel also matchs 10.10, so you must be running 10.10. I have seen where during some alpha/beta testing it has updated something incorrectly, so you may have that.

I ran 10.10 until 12.04 & then reinstalled. I changed to 64 bit when going from 9.04 to 9.10 which required a clean install. Now I only do clean installs.

Some have  found that after using Unity for a while, they then like it. Some of us are more stuck in the mud and resist that change.

gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 
12.04 LTS / Precise Classic (No effects) Tweaks and tricks
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)

---

### Post by Wilburight on 2012-09-17
> **oldfred said:**
> 
gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 
12.04 LTS / Precise Classic (No effects) Tweaks and tricks


Hmmm ... I'm interested! Probably time to do a fresh install and go 64 bit. Does the above offer any Compiz-like screen features, either inherently or as add-ons?

I like the way Compiz presently allows me to 'roll the cube' to separate my desktops/tasks. I have had Unity running on my netbook (Remix) for a year or more, but still can't find anything I like about it. Can't wait to get home to use my aging Ubuntu with an uncluttered desktop, spinning box and wavy windows.

Thanks for decoding what version of Ubuntu I'm running ;)

---

### Post by oldfred on 2012-09-22
I found this in my notes.

It's important to realize that Gnome classic and Unity (the standard Ubuntu DE) use the Compiz window manager, whereas both Gnome classic (no effects) and Unity-2D (aka: ubuntu-2D) use the Metacity window manager.


But I am running 2D, so I guess I really am running Metacity.

Comparison of desktop environments 
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)
All Desktops in one:
[http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu](http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu)
Both Unity and standard Gnome classic use Compiz as a WM, whereas Unity-2D and Gnome classic (no effects) use Metacity. Gnome shell and Cinnamon (which is a gnome-shell extension) use Mutter as a WM.

---

### Post by Wilburight on 2012-09-23
Thanks for the suggested reads.

I've yet to dive into this upgrade or even make a pre-update backup. Got iPad iOS6 upgrade issues to deal with today - *&%$# Apple!

---

