---
title: "Why do graphical root logins always fail?"
date: 2005-10-07
forum: Installation &amp; Upgrades
---

### Post by Comrade on 2005-10-07
Let's say I wanted to use network-admin.

If I access it from the menu, typing in my root password does not work for some reason. However, if I go to the terminal and su into root, I can run network-admin and everything works. 

Why can't I log in through the graphical dialog box? Have I misconfigured something? This is a new installation - I could not have eradicated anything in the kernel. 

It's just inconvenient to log in from the terminal all the time and run applications.

---

### Post by Dr. Nick on 2005-10-07
Ok, I have a few ?'s for you, Im on breezy but that shouldnt matter. First off ubuntu doesnt have a root account by default, did you make one? 
Try running it graphically and at the box enter your user pssword instead not the root password. How did you even set a root password anyway? Their shouldn't be any configuration needed for the graphical password prompt

---

### Post by mlomker on 2005-10-07
That's odd.  The password for **su** should be the same as **gksudo**.  Try *gksudo application* from the terminal next time and see if it works any differently.

---

### Post by smack on 2005-10-07
The program is probably just calling on su instead of sudo. I've got etherial installed and it does that. I have to do the same thing to use it, sudo -s then run it.

---

### Post by aysiu on 2005-10-07
[QUOTE=Comrade]
Why can't I log in through the graphical dialog box? Have I misconfigured something?[/QUOTE] Read this in full:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

