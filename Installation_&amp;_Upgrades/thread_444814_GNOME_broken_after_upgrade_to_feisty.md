---
title: "GNOME broken after upgrade to feisty"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by icefaerie on 2007-05-15
So, I recently upgraded to feisty.

After the install, I was able to log in via gdm and use gnome just fine.  Then I tried turning on Beryl, just for the heck of it.  (It hasn't worked in the past, but I was curious.) Beryl didn't really work (window decorations disappeared as usual), but that's okay.  I switched back to Metacity and quit Beryl.  Then I decided I wanted to play around with the themes.  So, I open the themes dialog.  I attempt to switch to "Brushed" and GNOME hung.  A bunch of Ctrl-Alt-Backspaces later, I killed gdm and rebooted.

When I rebooted, GNOME was no longer functional.  I tried logging in, and the splash screen came up, but nothing else happened.  There was also a white box, about 200x200, in the top left corner.  So, I killed gdm and tried Xfce, which works just fine.  I am posting from Xfce now, in fact.  But I decided to try GNOME again, and I got the same behavior.  I decided to leave it overnight.  When I came back, my computer had apparently restarted partway, and it was open to a root shell, with a bunch of bash errors about apt-get not being installed.  I Ctrl-d'd, and booting resumed normally.  gdm started, and I logged in to Xfce.

So, how do I make GNOME work again?

---

### Post by x64Jimbo on 2007-05-15
Short of backing up and reinstalling, you could try deleting the gnome configuration files in your home directory. Sometimes they just get buggered up and need to be started fresh. But if your system was having apt-related errors, it could be something more serious.

---

### Post by icefaerie on 2007-05-15
I am thinking that something other than gnome is seriously broken.

I don't know where the gnome config files are.  I tried to reinstall ubuntu-desktop.  That seemed to work.  I rebooted, but gnome still won't load from gdm.

As for the more serious problems, here's what I meant about it opening up a root shell on boot.

[IMG]http://img503.imageshack.us/img503/9410/img11061ff0.jpg[/IMG]

And often when I try to run a command, I get the following error.
```
bash: fork: Resource temporarily unavailable.
```

---

