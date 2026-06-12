---
title: "How do i get to the GUI login screen?"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by hanzj on 2005-10-13
I just upgraded to breezy. 

I rebooted my computer but it does not bring me back to the graphical welcome screen. What command do i use to go there?

By the way, I upgraded in the following order:
I upgraded with the following steps:
1.sudo apt-get update
2.sudo apt-get dist-upgrade
3. sudo apt-get install ubuntu-base ubuntu-desktop
4. a command like "sudo install -f" or something


One of the questions I had to answer was whether i wanted to use the current version of grub or install/use the newest one. I chose to get the newer one.


Thanks.

---

### Post by luckyaba on 2005-10-13
i think it's gdm

---

### Post by hanzj on 2005-10-13
luckyaba, thanks. I'll try gdm when I get home in 8 hours. I wonder why the upgrade didn't keep the process the same. How could I get my Ubuntu to always/automatically go to graphical login screen whenever I restart/reboot?

---

### Post by luckyaba on 2005-10-13
Not too sure. i would check your gdm.conf file
/etc/gdm/gdm.conf

---

### Post by musicman2059 on 2005-10-13
[QUOTE=hanzj]I just upgraded to breezy. 

I rebooted my computer but it does not bring me back to the graphical welcome screen. What command do i use to go there?

By the way, I upgraded in the following order:
I upgraded with the following steps:
1.sudo apt-get update
2.sudo apt-get dist-upgrade
3. sudo apt-get install ubuntu-base ubuntu-desktop
4. a command like "sudo install -f" or something


One of the questions I had to answer was whether i wanted to use the current version of grub or install/use the newest one. I chose to get the newer one.


Thanks.[/QUOTE]


Wasn't sudo apt-get-install ubuntu-base ubuntu-desktop supposed to be the first step?

---

### Post by hanzj on 2005-10-13
[QUOTE=musicman2059]Wasn't sudo apt-get-install ubuntu-base ubuntu-desktop supposed to be the first step?[/QUOTE]
I guess so, but when I checked out the instructions, it was the last step. Only after that did they change it to be the first step.

---

### Post by TheIdiotThatIsMe on 2005-10-14
I just upgraded to breezy, and found that my X had been broken (as has happened with a few users). For me it asks me to login and simply gives me a command line. If this is what is happening, then try:

```
sudo dpkg-reconfigure xserver-xorg
```

Then either reboot or type in:

```
sudo /etc/init.d/gdm restart
```
Note: If you use KDE like me it will be kdm restart instead.

Has always worked for me :p

---

### Post by hanzj on 2005-10-14
hey Idiot,
Will your tips make gui login henceforth load automatically everytime?

---

### Post by TheIdiotThatIsMe on 2005-10-14
[QUOTE=hanzj]hey Idiot,
Will your tips make gui login henceforth load automatically everytime?[/QUOTE]

Yep it should, it does on mine. Once you do the first bit with the reconfiguring X it will write it to the conf file and should load that way every time.

---

### Post by randlieb on 2005-10-14
[QUOTE=TheIdiotThatIsMe]I just upgraded to breezy, and found that my X had been broken (as has happened with a few users). For me it asks me to login and simply gives me a command line. If this is what is happening, then try: ```
sudo dpkg-reconfigure xserver-xorg
``` Then either reboot or type in: ```
sudo /etc/init.d/gdm restart
``` Note: If you use KDE like me it will be kdm restart instead. Has always worked for me :p[/QUOTE]

tried 'sudo dpkg-reconfigure xserver-xorg'  here's what it threw at me

/usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed

---

### Post by arj on 2005-10-14
[QUOTE=randlieb]tried 'sudo dpkg-reconfigure xserver-xorg'  here's what it threw at me

/usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed[/QUOTE]

If xserver-xorg is broken you might want to try ```
sudo apt-get -install --reinstall xserver-xorg
```

---

