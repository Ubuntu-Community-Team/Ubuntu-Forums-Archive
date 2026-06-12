---
title: "Giant fonts on login screen"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by mattlee on 2008-09-03
I installed Ubuntu yesterday successfully on my laptop (Compaq Presario V5214ea). However after the reboot the login screen had was unreadable due to the size of the font. I was able to login (you don't need to see what your typing to login). I then proceeded to install the kubuntu desktop (I've used Linux for years and prefer KDE) and switched from gdm to kdm. Again at the login I get the same problem, a giant font. The same problem showed up later with googleearth, which is unusable because of fonts size. The desktop and all other applications, so far, are normal.
Anybody got any clues? Which .config file do I have to change to get the login and googleearth to use a sensible font size?

---

### Post by pastalavista on 2008-09-03
You might check your usplash.conf file to see if the correct screen resolution is listed correctly.
```
sudo gedit /etc/usplash.conf

```
Change it to the correct resolution for your monitor --*[I]*[/I] if it's wrong. Then you need to save the changes and update the intramfs file.
```
sudo update-intramfs
```

Also, if that doesn't work, you could check to see if your proprietary graphics drivers are enabled.

---

### Post by mattlee on 2008-09-03
I checked the screen resolution, it's fine. The graphics associated with the login window looks fine. It's just the font

---

### Post by dBuster on 2009-04-09
can anyone shed some light on this old subject?  I too have recently installed Intrepid on my sisters older machine and the login screen fonts are HUGE!  I can not seem to locate any where to correct this outside of doing away with individual logins.  I have searched the forums and the internet to no resolution.  Tried the xorg.conf fix a try, gave the grub trick a try and each time failure to correct the fonts on the login screen.

I have another posting in the beginners section regarding this also...  But I am at my wits end..

---

### Post by gatewayasteroid on 2009-05-01
> **dBuster said:**
> can anyone shed some light on this old subject?  I too have recently installed Intrepid on my sisters older machine and the login screen fonts are HUGE!  I can not seem to locate any where to correct this outside of doing away with individual logins.  I have searched the forums and the internet to no resolution.  Tried the xorg.conf fix a try, gave the grub trick a try and each time failure to correct the fonts on the login screen.

I have another posting in the beginners section regarding this also...  But I am at my wits end..

Hi, it's a bug related to wrong screen DPI settings (bad hardware, basically).

I have a similar problem with an Asus VW161D screen.

See this bug report (among many others):
[https://bugs.launchpad.net/bugs/339572](https://bugs.launchpad.net/bugs/339572)

I solved installing slim as display manager and editing /etc/slim.conf:

```

davide@eeebox:~$ cat /etc/slim.conf 
# Path, X server and arguments (if needed)
# Note: -xauth $authfile is automatically appended
default_path        /bin:/usr/bin:/usr/local/bin:/usr/bin/X11
default_xserver     /usr/bin/X11/X
xserver_arguments   -nolisten tcp -dpi 100

...


```

Hope this helps someone...

---

### Post by theducks on 2009-08-02
I tried to add Eubuntu theme and everything to do wit login got messed up.
(I did manage switch back to the Ubuntu splash and Theme)

I am having the problem with the Greeter which comes after usplash is done.
I get about 72 point fonts INSIDE the login/password box AND if I click Options the text wil not fit on the screen. The screen looks normal until I start typing the username or password
Once I log in everything seems correct.
I gave checked gdm.conf.

Since no one is logged in, where are the settings kept for the greeter?

---

