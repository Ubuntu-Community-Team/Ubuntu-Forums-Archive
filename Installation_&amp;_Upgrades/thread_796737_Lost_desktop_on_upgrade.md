---
title: "Lost desktop on upgrade"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by jonrog63 on 2008-05-16
On upgrading to the new Ubuntu I have found that my desktop has completely disappeared and after logging on I am confronted with a blank screen - can I recover this???

---

### Post by randywilharm on 2008-05-16
It may not be as bad as it looks.

Try:

sudo apt-get install desktop

or

sudo apt-get install ubuntu-desktop


there may not be a hyphen in there
i can't remember

I had the same thing happen to me once
and this got the desktop back

---

### Post by zvacet on 2008-05-16
Maybe it is video card related,so you can try type in terminal 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

select **vesa** driver and you should have basic graphic.later you can go and search driver fo your graphic card.

---

### Post by djmasters on 2008-05-17
Same thing here, neither of the suggestions helped.   No interactive desktop on any user.  FWIW, same thing happened when I went from 6 to 7, ended up re-installing.

I get to a login screen, enter username & password, get HH background but nothing else.  No icons, no task bar, no right click.   If I press ctrl-alt-del AND wait about 30 seconds I will get that menu.  Choosing logoff returns me to the background and not back to a login screen.   Subsequent CAD's do nothing.

I can access the command line via alt-f2.   Tried creating a new user, no desktop for them either.

---

### Post by jonrog63 on 2008-05-23
I don't want to have to reinstall as I will lose data (some photos not backed up anywhere else) but at the moment I can't work out how to save them from the hard drive. Any thoughts?

---

### Post by djmasters on 2008-05-24
> **jonrog63 said:**
> I don't want to have to reinstall as I will lose data (some photos not backed up anywhere else) but at the moment I can't work out how to save them from the hard drive. Any thoughts?


Maybe not the easiest, but if you can get to the command line try enabling Samba, share the folder, and pull them off over the network to another system?   Just read up on enabling & using Samba if you're not familiar with it, it's pretty easy though.

Just an idea, I'm *not* very Linux savvy, I just know how to do what I've needed to do... which is create a NAS using the idea above.

---

### Post by jonrog63 on 2008-05-27
in the end dpkg --configure -a seems to have sorted it :)

---

### Post by RealMabu on 2008-06-24
Actually I have menu bar working and nautilus working.
Only the desktop won't work in the sense that it only displays the background.
I'd like to avoid the "dpkg --configure -a" because I'm afraid to wipe non-default configurations & settings. Is that true? Or is it safe to do?

*Cross post from [http://ubuntuforums.org/showthread.php?t=814079]("http://ubuntuforums.org/showthread.php?t=814079")*
> 
That was after an update that required a reboot.
I believe (but am not sure) that it was right after the release of 2.6.24-19-generic kernel.
So, symptoms:
-/home/myname/Desktop folder still exists and is in good health
-menu bar is fine too
-nautilus displays only the background and nothing can be done there (no new folder, no drag&drop)
-rebooting won't work for me
-under gconf-editor->apps->nautilus->preferences the "show desktop" checkbox IS checked. Tried to run gconf-editor as root also, same result: checked.

Oh, BTW, the OS is working fine, all apps run seamlessly and everything seems to be ok... just NO DESKTOP.

Any help?


---

### Post by The Brain on 2008-06-25
Same thing has happened to me. Have tried everything I can think of. Finally reinstalled via CD image. Still doesn't work. 

Gonna go out and buy windows tomorrow.

---

### Post by ardensdrunk on 2008-06-25
this happened to me after installing some updates

i ended up having to re-isntall the gnome panel from the command line (ALT + F1)

everything worked great after that.

---

### Post by RealMabu on 2008-06-30
> **ardensdrunk said:**
> this happened to me after installing some updates

i ended up having to re-isntall the gnome panel from the command line (ALT + F1)

everything worked great after that.

I'm too scared to lose my settings to go reinstalling the gnome panel.
Instead, I found a workaround:
1)ctrl+alt+f1 and text-mode login
2)sudo /etc/init.d/gdm restart
3)ctrl+alt+f7 if graphics-mode login doesn't appear.

It works for me.

---

