---
title: "Grub Messed Up"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by kirkquitar on 2007-09-29
I was dual booting XP and Feisty and I tried to install Ubuntu Gutsy Beta. 88% into the installation it froze, same thing happened twice so I gave up, and rebooted to get into windows. Grub shows up with an error 17, so I rebooted with the live cd to check it out. Turns out there is no grub folder in /boot - and therefore no menu.lst to edit. I've tried

grub-install hda

and

sudo grub
root (hd0,5)
setup (hd0)
--> gives an error.

So I guess I need a fresh install of GRUB, how do I go about doing that?

---

### Post by SpiritIsReality on 2007-09-29
howdy
ok, there be better than me around here to help you, but until one of them shows up, ...

when you tried to install to the ubuntu partition, and it failed, I'm pretty sure the partition
is in no condition to be installing the grub to the mbr, the master boot record, (hd0).
because the mbr has a grub that can no longer reach where it came from because it has
been formatted., you get the error message.

two choices.
one.
put the xp disc in, boot, when you get a chance to select fix the install or some such thing,
I'd have to check or google to tell you for sure,you can google fixmbr xp , ok here.
[http://www.google.ca/search?hl=en&q=xp+fixmbr&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=xp+fixmbr&btnG=Google+Search&meta=)
Recovery Console. that's it. then you will be able to boot micsoft.
two
install linux to the linux partition. if you were using the live cd and it stalls, then I would suggest
using the alternate cd, the proper one for your hardware.
 [http://us.releases.ubuntu.com/7.10/](http://us.releases.ubuntu.com/7.10/)

let me know what you think

trails

---

### Post by kirkquitar on 2007-09-29
I'm going to try fixing it by re-installing feisty, all I really need is windows back for now, I can upgrade when Gutsy is released. I'll let you know how it goes.

---

### Post by SpiritIsReality on 2007-09-29
ok 
sounds good.
because the live cd didn't work, I'd look into a thing or two to prepare for installing
with the alternate cd. and what to do if , once installed, you don't get a graphical user
interface (gui) windows. and instead get a command prompt login.
the short of it, you hold down Alt, press F2. that gets you a good place to log in at the 
command line. type your user name. enter. passwd. enter. then run
```
sudo dpkg-reconfigure xserver-xorg
```
before that happens, look for the vertical and horizontal refresh rates for the monitor you 
are using, either it's manual, or google it's name/model, or go to the manuf. homepage, support.
most all the questions it asks can be accepted at the defaults. except, how many MB ram on your 
video card, and what make it is. ati, or nv like that. If you're not sure, try the default. or vesa if that
doesn't work.
after it's done, you run
```
sudo shutdown -r now
```
to reboot, or
```
sudo /etc/init.d/gdm start
```
to start the gui. hopefully.
good place to check on that alternate install is hermanzone in australia.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
good roadmap for study is
[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059) and
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[https://help.ubuntu.com/community/TitleIndex](https://help.ubuntu.com/community/TitleIndex)

all the best
trails

---

### Post by lisati on 2007-09-29
> **kirkquitar said:**
> I'm going to try fixing it by re-installing feisty, all I really need is windows back for now, I can upgrade when Gutsy is released. I'll let you know how it goes.

I recently checked out Gutsy, and XP had disappeared from Grub's menu.....I'm part way through putting Feisty back (I didn't have the patiences to figure out the settings to get the Gnome desktop to show properly) and the install process recognized that XP was still there. It's possible that the pre-release version of the Gutsy installation CD still needs a bit of tweaking,

In other words, there's hope you'll get your dual boot working agin......

---

### Post by kirkquitar on 2007-09-29
I reinstalled Feisty, I'll try Gutsy again with the alternate cd when I have more patience. I don't have a problem with adding XP back to the GRUB menu, it's a simple edit to /boot/grub/menu.lst but the problem was that while installing Gutsy, it didn't get to the point where it installed GRUB before it crashed, so in /boot/ there wasn't even a GRUB folder. Anyway, everything is back in working order with Feisty, thanks for the help everyone.

---

### Post by SpiritIsReality on 2007-09-29
oh!
kirkquitar ...I  think in the grub manual I read where if there's a /boot you can install grub there? but at
88% install, I don't know if it would boot? the buds that wrote the install cd would probably know.
search : gnu grub manual
[http://www.google.ca/search?hl=en&q=gnu+grub+manual&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=gnu+grub+manual&btnG=Google+Search&meta=)
lisati ...you're right, there's hope. kirkquitar has dual boot working.
all the best
trails
buds

---

