---
title: "Unable to install Google Chrome on Ubuntu 20"
date: 2021-10-12
forum: Installation &amp; Upgrades
---

### Post by fckwan on 2021-10-12
I am new to Ubuntu. 
I installed a fresh copy of Ubuntu 20.04.3 on Virtual Box
When I downloaded the google-chrome-stable_current_amd64.deb and try to install using the Software install program. It say "Failed to install file: not supported"

Attached please find a copy of the screenshot.

---

### Post by grahammechanical on 2021-10-12
We install the Chrome web browser by downloading a Chrome installer package.

> Google Chrome is not preinstalled on Ubuntu by default, and you can&#8217;t install Chrome on Ubuntu using the *Ubuntu Software* app.

I got that quote from the OMG! Ubuntu web site along with these instructions.

[https://www.omgubuntu.co.uk/how-to-install-google-chrome-on-ubuntu](https://www.omgubuntu.co.uk/how-to-install-google-chrome-on-ubuntu)

Regards

---

### Post by MAFoElffen on 2021-10-12
You are both right. (Sort of). What I see in the photo is "Gnome Software"... which replaced the Ubuntu Software Store when it went away after 16.04. The old Ubuntu Software Sore was written in Python2.x, and Gnome Software was written in Python 3.x In 20.04, Gnome software was no longer a default installed app, because they were pushing the Snap Store. 

You can still manually install Gnome Software. If you do, then as before, if you DL a .deb from a browser, the user will be asked if they want to save or install.

Both the Ubuntu Store, and Gnome Software, are (partly) app installers. When the were installed, if you downloaded a .deb package in a browser, you were given the choice to save or open with one of those two app installers. I have instralled past version of chrome with the Ubuntu Software Store (years ago).

So what the OP is reporting, is that Gnome Software comes up with an error when trying to install the Chrome .deb.

Gnome Software is no longer a default installed app, "and" another method to install .deb package files is what grahammechical posted.

BUT, the current Google Chrome .deb installation package, what it actually does, is add's Google Chrome's Linux Repo's to the sources, then installs the current version using APT.

---

### Post by ActionParsnip on 2021-10-13
I suggest you use the
```

dpkg -i /path/to/filename.deb

```
command in a terminal to install Chrome. Obviously point to the actual deb file in your filesystem. The command above as-is will not work

---

### Post by VMC on 2021-10-13
> **ActionParsnip said:**
> I suggest you use the
```

dpkg -i /path/to/filename.deb

```
command in a terminal to install Chrome. Obviously point to the actual deb file in your filesystem. The command above as-is will not work

That's how I install it.


Run this to get the latest version, which is 94.0.4606.81-1:
```
wget --no-check-certificate https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

---

### Post by fckwan on 2021-10-15
Thanks for your help. The issue is resolved. I installed Google Chrome successfully

---

