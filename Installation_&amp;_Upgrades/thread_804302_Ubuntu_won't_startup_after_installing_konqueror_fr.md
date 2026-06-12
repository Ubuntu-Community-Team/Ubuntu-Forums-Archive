---
title: "Ubuntu won't startup after installing konqueror from repositories"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by speakeasy on 2008-05-23
I'm not sure at all what happened? I installed konqueror from the repositories followed what this thread says, [ubuntuforums.org/showthread.php?t=679697]("http://ubuntuforums.org/showthread.php?t=679697")
Now when it boots back up, nothing loads but the background shows up. I can't pull up anything!!! please help???

Edit: The post just explains how to get konqueror as default browser.

---

### Post by iaculallad on 2008-05-23
Try booting using the Recovery Mode (By Pressing ESC key when you see GRUB Loading ... on startup). This should give you a menu option to choose from.

Select the Recovery Mode and open up the terminal.

**sudo apt-get remove build-essentials**

Then, restart your PC. Check if you could start Ubuntu with no errors.

---

### Post by speakeasy on 2008-05-23
> **iaculallad said:**
> Try booting using the Recovery Mode (By Pressing ESC key when you see GRUB Loading ... on startup). This should give you a menu option to choose from.

Select the Recovery Mode and open up the terminal.

**sudo apt-get remove build-essentials**

Then, restart your PC. Check if you could start Ubuntu with no errors.


No it didnt do anything different.

---

### Post by iaculallad on 2008-05-23
> **speakeasy said:**
> No it didnt do anything different.

Same process as my first post, only this time use:

** sudo apt-get remove konqueror**

and restart

---

### Post by speakeasy on 2008-05-23
> **iaculallad said:**
> Same process as my first post, only this time use:

** sudo apt-get remove konqueror**

and restart

No still the same thing. I can boot into failsafe gnome though, and stuff works once again in failsafe but my xorg file seems to be messed up.

---

### Post by PmDematagoda on 2008-05-23
Log in to Ubuntu through fail-safe GNOME and then open up a terminal and do this:-
```
rm -r ~/.config ~/.gnome2
```
Keep in mind that this clears the GNOME configuration files, so you may have to reconfigure GNOME afterwards(it will be default).

---

### Post by speakeasy on 2008-05-23
> **PmDematagoda said:**
> Log in to Ubuntu through fail-safe GNOME and then open up a terminal and do this:-
```
rm -r ~/.config ~/.gnome2
```
Keep in mind that this clears the GNOME configuration files, so you may have to reconfigure GNOME afterwards(it will be default).

Umm, the terminal returns "No such file directory"... where are they supposed to be?

---

### Post by PmDematagoda on 2008-05-23
> **speakeasy said:**
> Umm, the terminal returns "No such file directory"... where are they supposed to be?

Hmm, seems to be the wrong command, they are hidden files located in the Home directory, so you can delete them with Nautilus for ease.

---

### Post by iaculallad on 2008-05-23
Using the same terminal, try this:

**rm -rf .gnome .gnome2 .gconf .gconfd .metacity**

---

### Post by speakeasy on 2008-05-23
> **PmDematagoda said:**
> Hmm, seems to be the wrong command, they are hidden files located in the Home directory, so you can delete them with Nautilus for ease.

Manually deleting did the trick thanks guys!!!

---

### Post by iaculallad on 2008-05-23
You're welcome. Go Ubuntu

---

