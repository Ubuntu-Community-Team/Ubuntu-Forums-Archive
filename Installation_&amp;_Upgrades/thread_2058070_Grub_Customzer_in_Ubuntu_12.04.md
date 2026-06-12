---
title: "Grub Customzer in Ubuntu 12.04"
date: 2012-09-14
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2012-09-14
Hello,

I'm already having many problems with 12.04.

*I can't find the command line.  Whatever happened to "sudo apt-get install xxxx."

*I can't change the text size in Grub, which is way too small for my HD screen.

*I can't get desktop cube to work.  I installed Compiz-Config-Settings-Mananger.

*I also want to use a tool called Grub Customizer, or Grub Configurator which will allow me to add a splash screen to grub and change the text color.  I really want to use this tool because I have some rad splash screens I want to use.

*Also, how do I show the desktop icons?

Please Help, Hannibal

---

### Post by wojox on 2012-09-14
> **coljohnhannibalsmith said:**
> 
*I can't find the command line.  Whatever happened to "sudo apt-get install xxxx."

Ctrl+Alt+T opens the terminal.

> **coljohnhannibalsmith said:**
> *I can't change the text size in Grub, which is way too small for my HD screen.


```
gksudo gedit /etc/default/grub
```
Look for and uncomment GRUB_GFXMODE
```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
```

> **coljohnhannibalsmith said:**
> 
*I can't get desktop cube to work.  I installed Compiz-Config-Settings-Mananger.
Did you enable the plugin?
> **coljohnhannibalsmith said:**
> *I also want to use a tool called Grub Customizer, or Grub Configurator which will allow me to add a splash screen to grub and change the text color.  I really want to use this tool because I have some rad splash screens I want to use.
PPA:
```
sudo apt-add-repository ppa:danielrichter2007/grub-customizer 
sudo apt-get update 
sudo apt-get install grub-customizer
```
> **coljohnhannibalsmith said:**
> *Also, how do I show the desktop icons?
```
gsettings set org.gnome.desktop.background show-desktop-icons true
```
Log out and back in

---

### Post by coljohnhannibalsmith on 2012-09-15
Thanks for the help.

*How do I get the menus back and select applications by menu?

*Is there an Ubuntu Classic feature in 12.04?

Thanks Hannibal

---

### Post by oldfred on 2012-09-15
gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 

12.04 LTS / Precise Classic (No effects) Tweaks and tricks
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)

---

### Post by coljohnhannibalsmith on 2012-09-15
Thanks Oldfred that worked for Gnome Classic.

Can you tell me how to get the Desktop Cube to work?

I also keep losing the upper or lower panel.  I was working on workspace preferences when this happened.

Thanks Hannibal

---

### Post by oldfred on 2012-09-15
Never used the cube nor saved any links on that.

---

### Post by coljohnhannibalsmith on 2012-09-15
Bump on Desktop Cube.

---

