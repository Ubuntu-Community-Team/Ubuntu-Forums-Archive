---
title: "Problems (un)installing ttf-lyx"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by thecaptainzap on 2010-01-21
First to introduce myself: I'm a computer-savvy person but I'm new to Linux. I'm running xubuntu 9.10. I searched around on this forum, and found some help regarding this problem, but it seems to be persisting.

So I made the mistake of trying to install LyX to work with LaTeX. During installation, my clown of an office-mate unplugged the power strip my computer was plugged into. Awesome.

After turning my computer back on, i went to a terminal and ran:
```
sudo dpkg --configure -a
```.

It mostly went alright, but gave me two error messages that said "E: ttf-lyx: subprocess installed pre-removal script returned error exit status 2" for both ttf-lyx and another component.

Following the advice on another thread ([http://ubuntuforums.org/showthread.php?t=1284523](http://ubuntuforums.org/showthread.php?t=1284523)) i ran the following:
```
sudo apt-get update
sudo apt-get-install -f
sudo dpkg --configure -a
sudo apt-get update
```.

This fixed one of the error messages, but "ttf-lyx" is quite stubborn. I don't mind forcing the entirety of "LyX" to uninstall as I've found another program I am happier using. No matter what I do in Package Manager or through the terminal, I still get an error message.

Thanks in advance for any help!!

---

### Post by thecaptainzap on 2010-01-22
Nobody has any ideas?

---

### Post by Leppie on 2010-01-22
you could try reinstalling the package using synaptic. go to Applications>System>Synaptic Package Manager, search for ttf-lyx, right click the package and select "Mark for Reinstallation", click the apply button.

---

### Post by thecaptainzap on 2010-01-22
I have tried using the package manager to reinstall, remove, and completely remove. When I do, I get the same message "E: ttf-lyx: subprocess installed pre-removal script returned error exit status 2."

-Tim

---

### Post by Leppie on 2010-01-22
there's a way to remove it completely, it involves removing the dependencies file etc.
don't remember the exact procedure, will search and get back.

---

