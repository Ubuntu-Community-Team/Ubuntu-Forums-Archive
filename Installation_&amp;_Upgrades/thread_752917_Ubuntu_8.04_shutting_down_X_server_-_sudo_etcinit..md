---
title: "Ubuntu 8.04 shutting down X server - sudo /etc/init.d/gdm stop (NOT WORKING)"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by ptutherow on 2008-04-12
I have seen this question answered several times as, open tty1 and type:```
sudo /etc/init.d/gdm stop
```and I am done. I have done this and I get a message that Gnome is stopping. However, There is still an X server running on tty7 and the nvidia drivers still won't install.```
sudo init  1
```
will shut the server down, but the driver asks for runlevel 3, runlevel 3 restarts the X server.

I can in fact install the driver with runlevel 1... but I would like to know the RIGHT way to do this. I have been hacking at it for days now, and would love to know the right answer. Thanks.

Additionally, is there a forum for 8.04 beta?

---

### Post by PmDematagoda on 2008-04-12
After running the command to kill X, did you try moving to a tty and then executing:-
```
sudo killall Xorg
```

---

### Post by ptutherow on 2008-04-13
After trying "sudo killall Xorg" ... from tty1, the system switches to the X server, which shuts down... then automaticly restarts. Now what?

---

### Post by mmmmm6mm6 on 2008-04-24
I've got this same problem i can't stop the GDM to install Nvidia driver.

---

### Post by zombix on 2008-04-26
sudo killall -9 Xorg

---

### Post by DaveBG on 2008-05-02
I think i have similar issue. I also need to install nVidia.

When i press Ctrl+Alt+Backspace my mouse stops and my screen locks on the wallpaper and nothing works except reset.

When i use the Ubuntu shutdown-> switch users command the same.
Logout from there the same.

Can someone help me?

ctrl+alt+f2 -> same all freeze no mouse.

```
sudo /etc/init.d/gdm stop
```
-> same all freeze no mouse.

> **zombix said:**
> sudo killall -9 Xorg

This does not freeze and just blanks my screen then i get the login prompt as usual when i boot the PC. I login and all is fine but X is running and i cannot install nVidia drivers...


Can someone help? maybe we have bug...

---

### Post by PmDematagoda on 2008-05-02
Boot Ubuntu in Recovery Mode, that way you get put into a terminal without the X-Server starting up.

---

### Post by DaveBG on 2008-05-02
> **PmDematagoda said:**
> Boot Ubuntu in Recovery Mode, that way you get put into a terminal without the X-Server starting up.


I run it this way and it gave me that cannot install in runlevel1 as will need to configure some deamons and i need to run it in runlevel3 (`telinit 3`)...

I ignored this but:

```
-> No precompiled kernel interface was found to match your kernel; would you li
  ke the installer to attempt to download a kernel interface for your kernel f
  rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
  this means that the installer will need to compile a kernel interface for
  your kernel.
ERROR: You do not appear to have libc header files installed on your system.
      Please install your distribution's libc development package.
```

And it does not install again :(


:(

---

### Post by PmDematagoda on 2008-05-02
Install the build-essentials package with:-
```
sudo apt-get install build-essential
```

Then try and install the driver.

---

### Post by DaveBG on 2008-05-02
I installed some modified driver from the Add/Remove applications and after enabling it and reboot all is OK.

X still crashes sometimes but rare now and i have enabled all beryl and 2560x1600 extras i wanted :)

10x!

---

### Post by PmDematagoda on 2008-05-03
> **DaveBG said:**
> I installed some modified driver from the Add/Remove applications and after enabling it and reboot all is OK.

X still crashes sometimes but rare now and i have enabled all beryl and 2560x1600 extras i wanted :)

10x!

Well, not wanting to burst your bubble here, but Beryl is rather old and has been replaced by Compiz-Fusion, so you may want to use that as it can also help in reducing crashes through using old and outdated compositing software.

---

### Post by DaveBG on 2008-05-06
> **PmDematagoda said:**
> Well, not wanting to burst your bubble here, but Beryl is rather old and has been replaced by Compiz-Fusion, so you may want to use that as it can also help in reducing crashes through using old and outdated compositing software.

Yes, i mean i enabled Compiz - the High graphics mode in ubuntu.

The problem is that i still have crashes when i try to restart X... No solution so far :(

---

### Post by husmear on 2008-06-16
hi!

i have installed the driver for my nvidia 6100 nforce driver but the maximum screen resolution is still 800x600, 640x480. i cant make it to 1024x768. i've tried to edit the xserver.conf but still the same. the distro i used is hardy.

please help..

i appreciate it very much.. thanks in advance..

---

