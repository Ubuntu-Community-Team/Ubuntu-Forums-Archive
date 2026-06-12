---
title: "[SOLVED] Command-line install to bare XFCE"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by tipp98 on 2006-12-19
Hello all, I ran into a bit of trouble while installing xubuntu. I am working with a Toshiba Satellite 4100XDVD (PII w/ 96MB ram). Upon text mode intall it would hang when installing anthy. Well, I found out anthy is not needed so I chose to do a command-line intall. My question is, how do I get from this point to doing a "startx" and having the desktop pop up? 

Currently When I startx all I get is X, and a fancy mouse pointer. I am trying to do this without installing the xubuntu-desktop package and only using the xubuntu alternate install CD(6.10). These are all of the packeges that I have installed and see as relevant. 

xorg
xfwm4
xfdesktop4
xcursor-themes
xfce4-icon-theme
xubuntu-system-tools
gtk2-engines-xfce
thunar

---

### Post by maxamillion on 2006-12-19
xfce4 would probably be the package that will get anything you might have missed including init scripts and files needed for "startx" to also start xfce because it itself is technically just a meta package that covers the dependencies of the different xfce4 modules.

post back if that doesn't work

---

### Post by kerry_s on 2006-12-19
sudo apt-get install gdm xfce4

---

### Post by tipp98 on 2006-12-19
ok, xfce4 is not on the xubuntu-alternat-6.10 CD. But, what apt-get tells you, upon install, that aptitude does not is that xfce4-panel replaces it. Sure enough, loaded aptitude and pulled up xfce4-panel and it says it replaces xfce4. xfce4-panel was already intalled so I went ahead and installed gdm.

Now I get a pretty login promt, but once I log in all I get is a solid color background with a pretty mouse. I found [this thread]("http://www.ubuntuforums.org/showthread.php?t=303319"), but I do not know the startup code for xfce. I think if I get this right it may work.

---

### Post by kerry_s on 2006-12-19
You must be doing something wrong, i've done the bare install lot's of times. That's start from the beginning ->

command-line install

login

sudo su

nano /etc/apt/sources.list
(comment(#) out the cdrom & uncomment all the repos,they start with deb> ctrl + x & y & enter to save)

apt-get update

apt-get install x-window-system-core gdm xfce4 mousepad synaptic

type> reboot

That's it, a barebones xfce4, the panel will be blank in the upper right corner & you should have a right click menu

---

### Post by tipp98 on 2006-12-21
> (comment(#) out the cdrom & uncomment all the repos,they start with deb> ctrl + x & y & enter to save)

If only I had a network card...

I'm not sure which package actually did it, but what I ended up doing was loading up aptitude, adding the xubuntu-desktop package, "g"oing, unselecting xubuntu-desktop and adding those items that looked like they might have an influence. I now have more or less what I wanted.

---

