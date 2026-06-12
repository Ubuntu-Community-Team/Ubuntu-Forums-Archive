---
title: "The greeter application seems to be crashing"
date: 2009-02-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by whoop on 2009-02-18
Upon booting (before login) I get:
The greeter application seems to be crashing. Attempting to use a different one.

I can click OK but it just restarts X and gives me the same message.

Anybody else has this? workaround?

---

### Post by oasick on 2009-02-18
Me too... same problem here :(

---

### Post by vvlist on 2009-02-18
+1

---

### Post by go7Ul1ai on 2009-02-18
+1

---

### Post by MacUntu on 2009-02-18
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/331292](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/331292)

Kdm and xdm work.

---

### Post by perlluver on 2009-02-18
Right I had to install KDM, sudo apt-get install kdm, gdm wouldn't start for me.

---

### Post by theSpaceAmoeba on 2009-02-18
+1

I booted via the "recovery" option in GRUB and chose Auto-fix graphics (it uses a vanilla xorg.conf file). This allows me to get into gnome, but I lose compiz and a bunch of other settings (including my Firefox extensions not working - don't know why). These losses persist even if I do a normal boot following the xorg.conf change.

I hope gdm-greeting is fixed real soon.

---

### Post by Vaun on 2009-02-18
I don't think installing KDM is the best advice in a GNOME environment with all of the additional dependencies.  You can CRTL > ALT > F1 (enter a virtual terminal)

```
sudo /etc/init.d/gdm stop 
startx
```

If you're daring and want to test the new GDM. 

[https://launchpad.net/~ubuntu-desktop/+archive/ppa]("https://launchpad.net/~ubuntu-desktop/+archive/ppa")

Add this to your sources list:

```
deb http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu jaunty main
```

```
sudo apt-get install gdm-new
```

This will uninstall gdm-guest-session fast-user-switcher applet and ubuntu-desktop.

It works as I'm using it now for testing with no greeter crash.

Uninstall gdm-new and --reinstall gdm if it doesn't work for you.

---

### Post by Kow on 2009-02-19
> **Vaun said:**
> I don't think installing KDM is the best advice in a GNOME environment with all of the additional dependencies.  You can CRTL > ALT > F1 (enter a virtual terminal)

```
sudo /etc/init.d/gdm stop 
startx
```

If you're daring and want to test the new GDM. 

[https://launchpad.net/~ubuntu-desktop/+archive/ppa]("https://launchpad.net/~ubuntu-desktop/+archive/ppa")

Add this to your sources list:

```
deb http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu jaunty main
```

```
sudo apt-get install gdm-new
```

This will uninstall gdm-guest-session fast-user-switcher applet and ubuntu-desktop.

It works as I'm using it now for testing with no greeter crash.

Uninstall gdm-new and --reinstall gdm if it doesn't work for you.

I have absolutely no input devices after switching to this new gdm and since the ubuntu devs thought it would be wise to disable ctrl+alt+backspace I have to cancel the gdm loader during init (since inserting a ctrl+alt+backspace with virtualbox has no effect.)

---

### Post by stovenator on 2009-02-19
I updated here [http://ubuntuforums.org/showthread.php?p=6760708](http://ubuntuforums.org/showthread.php?p=6760708) , but FYI downgrading libgtk2.0 resolved the issue for me.

---

### Post by Darko82 on 2009-02-19
For now i have solved removing gdm and installing slim.
But it is only a workaround

---

### Post by MacUntu on 2009-02-19
Will be fixed with the next update. If you can't wait: [https://launchpad.net/ubuntu/+source/gtk+2.0/2.15.4-0ubuntu3](https://launchpad.net/ubuntu/+source/gtk+2.0/2.15.4-0ubuntu3)

---

### Post by philinux on 2009-02-19
Installed KDM for now. Back up and running apart from user-switcher crashed.

---

### Post by Caseyjp on 2009-02-19
> **Kow said:**
> I have absolutely no input devices after switching to this new gdm and since the ubuntu devs thought it would be wise to disable ctrl+alt+backspace I have to cancel the gdm loader during init (since inserting a ctrl+alt+backspace with virtualbox has no effect.)


Kow, as to the ctrl+alt+bkspace  in virtualbox, you don't have to do that.  The keys to get to another shell =

ctrl+windows/ubuntu key+ f1 

now the gdm session will keep popping up, so keep saying okay to it.  Once you hit the bluescreen warning about display server being shutdown about 6 times in the last 90 seconds, you can then c/w/f1 to the shell and kill gdm with:

sudo /etc/init.d/gdm stop


Tis a kludge, but until its updated tis the quickest work around in virtualbox.

Further edit.  update just went up a couple hours ago.  issue appears resolved under virtualbox 2.1.4 anyway.

---

### Post by philinux on 2009-02-19
It's fixed now. Just updated.

---

### Post by ronacc on 2009-02-19
you beat me to the punch , cured here also with update .

---

### Post by philinux on 2009-02-19
LOL, kdm worked just the same for 15 mins.

---

