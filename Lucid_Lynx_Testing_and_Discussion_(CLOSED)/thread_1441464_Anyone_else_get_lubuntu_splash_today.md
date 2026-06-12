---
title: "Anyone else get lubuntu splash today?"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by shazbut on 2010-03-28
I just updated my lucid test box and had to restart it.  For some reason the startup/shutdown splash screens are showing the lubuntu artwork now.  Weird.

This is a standard ubuntu (gnome) install that i've tried to keep as 'vanilla' as possible.

---

### Post by Brian_the_King on 2010-03-28
> **shazbut said:**
> I just updated my lucid test box and had to restart it.  For some reason the startup/shutdown splash screens are showing the lubuntu artwork now.  Weird.

This is a standard ubuntu (gnome) install that i've tried to keep as 'vanilla' as possible.
Same thing happened to me earlier but I can't imagine why.

---

### Post by jeremy1138 on 2010-03-28
> **shazbut said:**
> I just updated my lucid test box and had to restart it.  For some reason the startup/shutdown splash screens are showing the lubuntu artwork now.  Weird.

This is a standard ubuntu (gnome) install that i've tried to keep as 'vanilla' as possible.

I have a MythBuntu splash when I start up/shut down my computer.  Don't know what the deal is with that.  Anyone else having this problem?

---

### Post by Arand on 2010-03-29
[https://bugs.launchpad.net/ubuntu/+source/netbook-meta/+bug/550237](https://bugs.launchpad.net/ubuntu/+source/netbook-meta/+bug/550237) is the relevant bug for this issue.

Instructions for recovery are on the report:
> Updated plymouth package with corrected recommends is on the line.

***For anyone hit by this bug you will need to manually install the package:
plymouth-theme-ubuntu-text

And then remove these packages:
lubuntu-plymouth-theme
mythbuntu-default-settings

***If you are stuck with a black desktop after boot:
Switch over to a terminal via CTRL+ALT+F2

Login and run the commands:
sudo aptitude remove mythbuntu-default-settings
sudo aptitude install plymouth-theme-ubuntu-text
   (above command will also auto-remove several xfce-related packages)

and finally reboot.
- Arand

---

### Post by shazbut on 2010-03-29
Thanks, Arand.  I just assumed the problem would go away with the next round of updates.  Obviously not.

---

### Post by 3rdalbum on 2010-03-29
Haha, yeah I got the Lubuntu one today and was mighty mystified. I thought something I'd installed had pulled in the Lubuntu splash.

It reminded me of the guy who posted in Absolute Beginner Talk asked for "urgent" help because he had installed the Debian splash screen and couldn't figure out how to get back the Ubuntu one.

---

