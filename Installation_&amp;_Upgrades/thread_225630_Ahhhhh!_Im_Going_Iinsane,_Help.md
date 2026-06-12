---
title: "Ahhhhh! Im Going Iinsane, Help"
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by Roflcopterrr on 2006-07-30
I have just installed Ubuntu Alternative on my Computer for the first time, and I ALWAYS GET BOOTED INTO A COMMAND PROMPT LIKE THING!!! WHERE IS THE GUI??


I have tried sude /etc/init.d/gdm start BUT IT SAYS COMMAND NOT FOUND!!!

I have done sudo dpkg-reconfigure xserver-xorg BUT IT SAYS XSERVER-XORG IS NOT INSTALLED!!

WHY??!?!?


I'VE BEEN TRYING THIS FOR 3 HOURS, NOTHING WORKS!!

---

### Post by Jagot on 2006-07-30
You didn't happen to download the server version by accident did you?  Try:

```
startx
```

Failing that:

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by Roflcopterrr on 2006-07-30
I did download the server verision...
Isn't this what you need for a LAMP server??



:confused: :confused:

---

### Post by Jagot on 2006-07-30
Yep - but the server has no GUI - everything is done from command prompt.

If you need a graphical user interface then follow the instructions to install the ubuntu-desktop package.

---

### Post by Roflcopterrr on 2006-07-30
So, you want me to burn a new ISO?

---

### Post by Jagot on 2006-07-30
No - you can download the package you need from the repos.  From the command prompt do this:

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by Roflcopterrr on 2006-07-30
Do I need my ethernet cable plugged in? 

When I do plug it into my server computer, my laptop's connection goes down for some reason.

---

### Post by Jagot on 2006-07-30
Yep - you'll have to be connected to the Internet - it will download from Ubuntu's online repositories.

---

### Post by Roflcopterrr on 2006-07-30
Aha - When I do plug it in, my entire network loses connection!

---

