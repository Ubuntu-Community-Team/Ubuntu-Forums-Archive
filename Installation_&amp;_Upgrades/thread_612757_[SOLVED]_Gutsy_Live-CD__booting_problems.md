---
title: "[SOLVED] Gutsy Live-CD / booting problems"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by perixx on 2007-11-14
I've got an ATI X1950GT card (really annoying piece of hardware, not only under Linux, that is).


I figured out that my Gutsy LiveCD will not boot at all when I manually choose 1280x1024 16/24k at the bootup. Only booting with 1024x768 will succeed - unless I let it boot itself, then I have a much higher resolution availible (1600x1200). Changing the language will cause the booting to interrupt, leaving me with some booting messages; when I do a manual 'startx' the X-server will start the desktop.
[COLOR="Blue"]Edit:
In rare cases, Booting actually does end up in an active X-server, but only with 800x600 resolution and an objectonable tiny & crippled font display; I have to switch to a virtual desktop (ALT+F5) and do 'startx' to finally get 1600x1200 of resolution at the start and good font quality...
Funny thing is, I can't switch to 1280x1024, only to 1024x768 and below. But never back up to 1600x1200 again. [/COLOR]

I've tried both Ubuntu 64AMD and Xubuntu 64AMD and it seems the Xfce version is more compatible and less troublesome in my system at the bootup...

Btw, I cannot get Mint 4.0 Live-CD to boot on my system, 3.1 (Celena?) will behave similar to Gutsy's Live-CD, but work so-so.

Maybe booting with 'noapic nolapic' switches will help, got to try it -- switching off ACPI in the BIOS will not change anything. Of course, I dont't know, if it's really my graphics card or the OS that makes trouble...




perixx

---

### Post by perixx on 2007-11-21
***bump***

---

### Post by perixx on 2007-12-20
I'll have to doublecheck, but I haven't tried the live-CD after connecting both the digital and analog signal cable of my TFT; it's very likely that I just got stock at the 'invisible' gdm login with an obviously blank screen - while Ubuntu had activated the ANALOG signal out of my graphics card... 

Anyway, the awkward fonts on the desktop are a different story!

perixx

---

### Post by perixx on 2008-01-04
Just for the sake of rounding up things, one of these problems could be involved - in this case it's definitely the ANALOG/DIGITAL output switching problem.  

[http://ubuntuforums.org/showthread.p...g+booting+time]("http://ubuntuforums.org/showthread.p...g+booting+time")
I've also encountered an issue with the live-CD for some weird reason activating the ANALOG/2nd video out of my graphics card at boot-up, instead of the digital out - or the switching of connectors during operation while graphics the mode is changed.

I also have this problem under XP when loggin in, so it's maybe related to ATI cards/drivers...

Did you try to switch between virtual terminal and X-server with CTRL+ALT+F1, respectively +F7?
If you can't open the X-server (graphical login) automatically, I'd try to use the first combination, opening a virtual terminal
and using either one of those commands:
```
startx
sudo /etc/init.d/gdm restart
```
another possibility, if System is already installed: in the file /boot/grub/menu.lst, the command
```
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/[partition] ro **[COLOR="Blue"]quiet splash[/COLOR]**
```
is missing the coloured options; you can change this by going into the virtual terminal and do
```
sudo nano /boot/grub/menu.lst
```
then alter the command as needed and 
save+quit with CTRL+X.

perixx

---

