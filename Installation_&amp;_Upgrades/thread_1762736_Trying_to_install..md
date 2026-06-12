---
title: "Trying to install."
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by sportcrazy60 on 2011-05-19
I have WinXP Home Edition on a old computer. Display card is Ti4200 and it shows me the console during startup then blank screen.
I think this may be to do something with my nonfunctional cddvd drives) all connected,no working,they have power and spin the disc)Tried accessing console (Crtl+Alt+f1),no help.I can boot to Window$ normally. I really want to try the new Ubuntu. I installed it with Wubi.

---

### Post by jerrrys on 2011-05-20
looks like your video card is no longer supported.  from what i read, ubuntu 10o4 will give you generic support

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Ti4200&as_qdr=all&sa=Google+Search&lang=en#812](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Ti4200&as_qdr=all&sa=Google+Search&lang=en#812)

---

### Post by sportcrazy60 on 2011-05-20
I got it to start by selecting ACPI workarounds. >Befire that i reinstalled. It may also be due to a corrupt installation of Ubuntu.

PS It drops me to shell,shows this screen and ten a black screen.

---

### Post by PowerBarry43 on 2011-05-20
Are you sure its a blank screen when i installed ubuntu there was no backlight so i thought it was blank for ages then  i noticed it was just really faint.

I managed to fix it by connecting it to a bigger screen and setting the graphics to a lower resolution.

you could also try using the safe graphics mode when booting

hope that helps

Barry

---

### Post by sportcrazy60 on 2011-05-20
CRT,works perfec with window$. It shos the command line as it loads the system. Can yyou diagnose from that error I photographed?

---

### Post by jerrrys on 2011-05-20
if your reinstalling and want to turn off acpi, i think its F6 at the start of the install. but not sure

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=turn+off+acpi&as_qdr=all&sa=Google+Search&lang=en#881](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=turn+off+acpi&as_qdr=all&sa=Google+Search&lang=en#881)

---

### Post by sportcrazy60 on 2011-05-20
Well i can access the prompt. It shows (initramfs) as the "user". The different TTYs show as DOS-like, blank.What can I do???
PS. I give up. I'll get 10.04.
10.04 throws me in the shell too. But this time no errors,just the initramfs shell.cant start x using "startx" command. TTy7 has no errors. How can I advance?

---

### Post by sportcrazy60 on 2011-05-20
Or I coluld install only Ubunu because i got my dvd drives to work...

---

### Post by sportcrazy60 on 2011-05-21
Surprise... New problems. I burnt a 10.04 disc. Then I booted from it and got:
BusyBox v 1.13.3 -Ubuntu 1:13.3-1UBUNTU 11 BUILT-IN SHELL(ASH)
Enter "help" for a list of built-in commands.
(initramfs) Unable to find a medium containing a live filesystem
(i typed it) ubiquity
/bin/sh:ubiquity:not found
(initramfs)

HELP!
EDIT: Trying DEbian installer.

---

### Post by sportcrazy60 on 2011-05-21
Does the same with debian installer/cd.

---

### Post by Dutch70 on 2011-05-21
Download & try the alternate cd install. If that doesn't work, you may want to try the minimal cd install. 

It sounds like you're working with older hardware & Xubuntu or Lubuntu (in that order) may be a better option for you. Both are very nice.
Ubuntu "recommends" 1GB minimum of RAM. Although some run it with 512MB & they say it works fine.
Xubuntu recommends 512MB.
Lubuntu will run on a toaster...:D ...lol j/k
Actually, less than 256MB.

[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/Installation/SystemRequirements[/COLOR]]("https://help.ubuntu.com/community/Installation/SystemRequirements")

---

### Post by sportcrazy60 on 2011-05-21
> **Dutch70 said:**
> Download & try the alternate cd install. If that doesn't work, you may want to try the minimal cd install. 

It sounds like you're working with older hardware & Xubuntu or Lubuntu (in that order) may be a better option for you. Both are very nice.
Ubuntu "recommends" 1GB minimum of RAM. Although some run it with 512MB & they say it works fine.
Xubuntu recommends 512MB.
Lubuntu will run on a toaster...:D ...lol j/k
Actually, less than 256MB.

[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/Installation/SystemRequirements[/COLOR]]("https://help.ubuntu.com/community/Installation/SystemRequirements")
Well I think it is because of the kernel It shows the udevd errors when trying Debian too. And DSL´sx window system doesnt start with default derver,it needs to me the other server. This is a Linux problem,not memory. I have 1gb of mem.

---

### Post by Dutch70 on 2011-05-21
Ok, that's all good, but did you try my first suggestion? 

To download & try the alternate cd install.

---

