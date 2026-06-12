---
title: "Xserver not working"
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by ogu on 2005-05-14
hello. i just installed ubuntu, and just after the installation, when XServer was supposed to load, it gives me an error... i checked the log and these are the errors:

```
(EE)I810(0): Cannot Read V_BIOS
(EE)I810(0): VBE initialization failed
(EE)screen(s): found, but none have a usable configuration

Fatal server error:

No Screens found
```

after the installation, if i try to boot, i can't even get to bash ... i have to re-install.

here are some tech specs of my comp:

Installing on a 10.2G Samsung HD
Pentium Celeron 1.8Ghz
256M Ram

my monitor is a 21 inch Dell sony trinitron.

any help will be appretiated.

---

### Post by Hokputooy on 2005-05-14
What Video card do you have?

---

### Post by nad on 2005-05-14
At the bootup menu selection screen, choose "recovery mode". This will get you to a command prompt. From here, we may be able to repair your installation.

What is your video card/hardware?

---

### Post by ogu on 2005-05-14
[QUOTE=Hokputooy]What Video card do you have?[/QUOTE]

ATI Radeon 9200

>  	At the bootup menu selection screen, choose "recovery mode". This will get you to a command prompt. From here, we may be able to repair your installation. 

i'll try that ... i'll edit after i do it.

thank you :)

---

### Post by nad on 2005-05-14
Hello again,

If you are ready, you can begin with these two commands.

sudo dpkg-reconfigure xserver-xorg

You will be prompted for your password. Please note any errors.

sudo /etc/init.d/gdm restart

Any luck?

---

### Post by ogu on 2005-05-14
[QUOTE=nad]Hello again,

If you are ready, you can begin with these two commands.

sudo dpkg-reconfigure xserver-xorg

You will be prompted for your password. Please note any errors.

sudo /etc/init.d/gdm restart

Any luck?[/QUOTE]

thanks a lot nad! i ran the configure, and it was really simple... thanks for pointing to that. now i'm typing this from ubuntu ;).

i owe you one.

---

### Post by nad on 2005-05-15
Your welcome.

Make a backup copy of your good /etc/X11/xorg.conf file in case you ever need it.

The next time you are in NY you can buy me a beer.

---

