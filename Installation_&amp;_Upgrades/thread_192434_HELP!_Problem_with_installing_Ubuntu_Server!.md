---
title: "HELP! Problem with installing Ubuntu Server!"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by Isoss on 2006-06-08
I have downloaded ubuntu server 6.06 and burn an iso CD and installed it. After the installation is done it rebooted and at the GRUB I chose the first selection and then it took me to a terminal and no graphical system was booted! I don't really remember what it was telling but something like this, booting kernel and then it told me that something wasn't detected and then it asked for the logins and now I am in something like the recovery mode!

What is that? Why can't I continue to login my desktop?

---

### Post by Isoss on 2006-06-08
ok, to make it easier, I guess after selecting the first selection at the GRUB it gives me this:
Uncompressing... ok booting the kernel
then "something" not detected then asks for the logins.

I am able to apt-get here, I am trying to install gdm so maybe this would help loging in a desktop!
I prefer your help though, cuz I am afraid there might be a problem!
So please help!

---

### Post by taurus on 2006-06-08
If you now decide to have a window manager, then
```

sudo apt-get install ubuntu-desktop <-- for Gnome
sudo apt-get install kubuntu-desktop <-- for KDE
sudo apt-get install xubuntu-desktop <-- for XFce

```
Maybe you need to look in /var/log/messages to see exactly what's wrong with the system when it boots...
```

more /var/log/messages
-or-
sudo more /var/log/messages

```

---

### Post by Ocxic on 2006-06-08
You instaled a server, there is no graphical eviroment, just the command line, do what taurus said and I't set you right.

---

### Post by Isoss on 2006-06-09
Oh! sorry, I didn't know that! I was just searching online and one of the websites was showing some screen shots for ubuntu and talking about ubuntu server so I thought it's a normal desktop!

---

