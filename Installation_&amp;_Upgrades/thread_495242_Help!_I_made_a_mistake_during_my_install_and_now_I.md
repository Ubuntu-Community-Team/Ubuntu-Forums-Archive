---
title: "Help! I made a mistake during my install and now Im stuck without a GUI"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by Anorath on 2007-07-07
Well, i sure feel dumb. Would you believe this is the second time this has happened to me? I'm currently home from university and I am stuck with only my laptop for my computer needs. I decided to go about installing Ubuntu on it. I had it on once before but due to some problems with the courses I was taking in school I needed to reinstall windows for some programs that would not run well in WINE. 

Anyway, now that I no longer have to worry about that I wanted to go back to Ubuntu. Now my laptop isnt too old but my internal cd drive broke a few months back and since then I have been using an external cd drive. My laptop does not support booting from a usb cd drive so I followed the instructions in the online documents section for installing from windows (copy contents of alt install cd to hard drive, install GRUB for windows and edit the boot.ini file to boot from the copied files which then changes to a cd install from the external drive.) 

But leave it to me to be rushing myself and at the screen to select the "Ubuntu Desktop" i mistakenly pressed enter instead of selecting it (why is it not selected in the first place anyway?) So now I am stuck without a GUI desktop.

Normally I would just restart the install but without a bootable cd drive this is impossible.

I know there is a way to fix this, but at the moment I am at a loss. Please, any help would be much appreciated. I have searched but I cannot find any people with this problem (i guess Im the only linux newbie that would make this mistake)

Thanks,

Anorath

---

### Post by taurus on 2007-07-07
What happens if you run this command from a prompt, after you've logged in?

```
startx
```
Otherwise, install Gnome if you have access to network.

```
sudo aptitude update
sudo aptidude install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by kknd on 2007-07-07
You can try to install the ubuntu-desktop package (for gnome):

sudo aptitude install ubuntu-desktop.

**P.S: ** When I was typing, there wasn't any reply, sorry for the "spam".

---

### Post by Anorath on 2007-07-07
Nothing happens when i type startx.

As for the rest of it, thats what I thought to do, but I have no internet access on the computer.
I do have the alt install cd in my external drive, but how do I tell it to look there for the files?

Thanks,

Anorath

---

### Post by Anorath on 2007-07-07
Nevermind then, I believe I have it figured out. For some reason my leptop would see my external drive until i turned it off and on again.

Thanks

Anorath

---

### Post by dougfractal on 2007-07-07
sudo dpkg-reconfigure -phigh xserver-xorg

---

