---
title: "This is not a problem with Ubuntu!"
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by OfficeLinebacker on 2006-03-04
It's a problem with the way I am doing something.

After installing Ubuntu, I just get a command line login.  I;m not familiar enough with the environment (I work in RedHat with lots of bells and whistles like lynx and such.  Anyways I am lazy and would like the gnome.

So what did I do wrong?  After all that work all I have is a command line.

---

### Post by andlinux21 on 2006-03-04
did you just hit enter and do a plain install or did you do a server install?
If you are not sure you can do a sudo apt-get install ubuntu-desktop and see what you get

---

### Post by codejunkie on 2006-03-04
[QUOTE=OfficeLinebacker]It's a problem with the way I am doing something.

After installing Ubuntu, I just get a command line login.  I;m not familiar enough with the environment (I work in RedHat with lots of bells and whistles like lynx and such.  Anyways I am lazy and would like the gnome.

So what did I do wrong?  After all that work all I have is a command line.[/QUOTE]
if you did a server install it has no gui installed by default because it just wastes resources. 
if you did a normal then my money is on your video card not being setup correctly what kind is it?

---

### Post by OfficeLinebacker on 2006-03-04
[QUOTE=andlinux21  ]  did you just hit enter and do a plain install or did you do a server install?[/QUOTE]

pretty sure I hit enter but my mind is fuzzy so I can't say for sure
[QUOTE=andlinux21  ] If you are not sure you can do a sudo apt-get install ubuntu-desktop and see what you get?[/QUOTE]


Well lots of crap scrolled by and the CDROm and HD are going nuts so I think that's a positive sign

Thanks for the advice guys!

---

### Post by aysiu on 2006-03-04
If you accidentally did a server install, try typing this at the command-line ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
```

---

### Post by OfficeLinebacker on 2006-03-04
Hey guys looks like I DID accidentally do the server install, but the apt-get didnt' work, I just did a fresh install.  Posting from 5.10 as we speak.

Now trying to get FOlding@Home sorted out.

Thanks for the help guys

---

