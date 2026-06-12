---
title: "Just installed Studio 10.10 no GDM theme."
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by alias_neo on 2010-11-08
I just removed my previous linux install and installed Ubuntu Studio because of the nicer look.

However the login screen is still the borin plain one. I have been to the "Login Screen" and tried to select theme as mentioned but it doesn't have any tabs or info for it.

I have checked that all ubuntu-studio packages are installed, what am I missing?

---

### Post by cipherboy_loc on 2010-11-08
Go to the first tty (ctrl+alt+f1) and log in (type you username, hit enter, type your password, hit enter). Once the command line starts, run:

```
export DISPLAY=':0.0' ; sudo -u gdm gnome-control-center
```

Change back to GDM (ctrl+alt+f7), and under appearance, change the themes, background wallpaper, etc.

Close out of the windows once you get it styled, and go back to the first tty (ctrl+alt+f1). Type:

```
logout
```


Then go back to GDM (ctrl+alt+f7) and view your new login screen. It is important to logout before using GDM again, just to make sure you don't have any un-needed sessions open. Its more of a security thing....





Cipherboy

---

### Post by alias_neo on 2010-11-08
> **cipherboy_loc said:**
> Go to the first tty (ctrl+alt+f1) and log in (type you username, hit enter, type your password, hit enter). Once the command line starts, run:

```
export DISPLAY=':0.0' ; sudo -u gdm gnome-control-center
```

Change back to GDM (ctrl+alt+f7), and under appearance, change the themes, background wallpaper, etc.

Close out of the windows once you get it styled, and go back to the first tty (ctrl+alt+f1). Type:

```
logout
```

Then go back to GDM (ctrl+alt+f7) and view your new login screen. It is important to logout before using GDM again, just to make sure you don't have any un-needed sessions open. Its more of a security thing....





Cipherboy

I tried this, but pressing CTRL+ALT+FX doesn't take me to TTY, I'm on the desktop, I have tried all F-Keys, it does nothing.

EDIT: VMWare intercepts the CTRL+ALT so I can't use this method to switch to tty, is there a command line method? I tried "chvt 1" and the system hung.

---

### Post by cipherboy_loc on 2010-11-08
If you launch it from the terminal:

```

cipherboy@cipherboy-workstation:~$ sudo -u gdm gnome-control-center --display=':0.0'
No protocol specified
Cannot open display: :0.0

```

The issue being that GDM does not own the X session, cipherboy (or whatever your user name is...) owns it.



Cipherboy

---

### Post by gonger on 2010-11-09
> **cipherboy_loc said:**
> If you launch it from the terminal:

```

cipherboy@cipherboy-workstation:~$ sudo -u gdm gnome-control-center --display=':0.0'
No protocol specified
Cannot open display: :0.0

```

The issue being that GDM does not own the X session, cipherboy (or whatever your user name is...) owns it.



Cipherboy

This worked for Me , ubuntu 10.10. Make sure you logout of gdm/X session before switching to TTY1:)

---

