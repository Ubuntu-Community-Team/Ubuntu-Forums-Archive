---
title: "gdm going beserk"
date: 2009-07-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nanog on 2009-07-20
After recent updates gdm has become corrupt. The login field is distorted and greeter icons are Xed out. I can still login by using tab and manually typing in an invisible password. The gnome environment loads but becomes corrupt with the panel flashing on and off continuously without loading icons. Gnome-do works but some of the icons are Xs. I get no errors after killing and restarting the panel and nautilus but when I restart the gnome-settings-daemon I get:

```
GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
```

A peak at var/log/gdm:0-greeter.log shows the same error along with cascade of theme/icon errors.
 
I've purged and reinstalled all of gdm and ubuntu-desktop but still get the same errors.

---

### Post by nanog on 2009-07-20
Anyone else getting this?

---

### Post by wayne_cat on 2009-07-20
I also have theses error messages:

```
GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
```in the gdm log files and in .xsession-error ... but no problems with gdm.

edit:

what happens if you disable gdm ... startx to start gnome ... maybe this is not a gdm problem.

---

### Post by rtalcott on 2009-07-20
same here...sort of...but I can boot into the command line.
rt

---

### Post by Naddiseo on 2009-07-20
> **nanog said:**
> Anyone else getting this?

Yes, can you bug it, and I'll confirm.

---

### Post by qwertyu on 2009-07-20
Same problem here!
Let's hope they put an update to fix it soon...
Usually that's what happens, just wait for the update and everything is fixed easly...

---

### Post by tghe-retford on 2009-07-20
> **nanog said:**
> The gnome environment loads but becomes corrupt with the panel flashing on and off continuously without loading icons. Gnome-do works but some of the icons are Xs.
I managed to get to the desktop after upgrading, and it gets far worse. It's totally unusable, all the icons have defaulted to blank files or files with a X in them, the panel is completely broken and themes completely broken. Restarting the PC has finally borked gdm to the point where only the bottom menus for languages, keyboard and session work. I'll add a me too to your bug report.

---

### Post by rtalcott on 2009-07-20
> **tghe-retford said:**
> I managed to get to the desktop after upgrading, and it gets far worse. It's totally unusable, all the icons have defaulted to blank files or files with a X in them, the panel is completely broken and themes completely broken. Restarting the PC has finally borked gdm to the point where only the bottom menus for languages, keyboard and session work. I'll add a me too to your bug report.

That is EXACTLY what I see...
rt

---

### Post by Naddiseo on 2009-07-20
This look like the relavent bug repot: [https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/401938](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/401938)

---

### Post by tjeremiah on 2009-07-20
> **qwertyu said:**
> Same problem here!
Let's hope they put an update to fix it soon...
Usually that's what happens, just wait for the update and everything is fixed easly...

how am I suppose to update? Once I finally figured out how to log in, nothing works. Internet, nothing.

---

### Post by qwertyu on 2009-07-20
Boot in Safe mode and do Apt-get update, apt-get upgrade

I just checked and in about half an hour there will be an updated package of gtk+, let's see if it does the fix...

---

### Post by tjeremiah on 2009-07-20
> **qwertyu said:**
> Boot in Safe mode and do Apt-get update, apt-get upgrade

I just checked and in about half an hour there will be an updated package of gtk+, let's see if it does the fix...

safe mode? Ive never noticed an option for safe mode :(

---

### Post by amauk on 2009-07-20
virtual terminals
(crtl+alt+F1, crtl+alt+F2....)

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by nanog on 2009-07-20
I figured it was something to do with the gtk packages. I tried to take a desktop pic for a bug report but got this strange error about pngs not being supported.

I've found that terminating gnome-settings-manager stops the flickering panels and nautilus reboots. It gives you a bizarre looking but useable desktop. KDE (but not xubuntu) works so thats what i am using until they fix this. 

For the person without network connectivity you should be able to get a network root in recovery mode and get updates via eth0. Hopefully you have ethernet available. Another option would be to manually turn on wireless in in a terminal (ctrl+alt+F1,[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)). On my two affected laptops wireless works in  (at least after I kill the settings-manager).

---

### Post by budluva04 on 2009-07-20
gtk+2.0 (2.17.5-0ubuntu2) karmic; urgency=low

  * Try a no change upload to see if that fixes the amd64 loader issue

Date: Tue, 21 Jul 2009 00:16:12 +0200
Changed-By: Sebastien Bacher <seb128@ubuntu.com>
[https://launchpad.net/ubuntu/karmic/+source/gtk+2.0/2.17.5-0ubuntu2](https://launchpad.net/ubuntu/karmic/+source/gtk+2.0/2.17.5-0ubuntu2)



it's coming, packages are built, just waiting on repo's to sync...

apt-cache policy libgtk2.0-0
libgtk2.0-0:
  Installed: 2.17.5-0ubuntu1
  Candidate: 2.17.5-0ubuntu1
  Version table:
 *** 2.17.5-0ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
        100 /var/lib/dpkg/status

just keep waiting i guess :P

---

### Post by tjeremiah on 2009-07-20
> **budluva04 said:**
> gtk+2.0 (2.17.5-0ubuntu2) karmic; urgency=low

  * Try a no change upload to see if that fixes the amd64 loader issue

Date: Tue, 21 Jul 2009 00:16:12 +0200
Changed-By: Sebastien Bacher <seb128@ubuntu.com>
[https://launchpad.net/ubuntu/karmic/+source/gtk+2.0/2.17.5-0ubuntu2](https://launchpad.net/ubuntu/karmic/+source/gtk+2.0/2.17.5-0ubuntu2)



it's coming, packages are built, just waiting on repo's to sync...

apt-cache policy libgtk2.0-0
libgtk2.0-0:
  Installed: 2.17.5-0ubuntu1
  Candidate: 2.17.5-0ubuntu1
  Version table:
 *** 2.17.5-0ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
        100 /var/lib/dpkg/status

just keep waiting i guess :P
ill wait an hr.

---

### Post by budluva04 on 2009-07-20
repo's are updated, good to go now :P

---

### Post by hanzomon4 on 2009-07-20
Hey.. hey, GDM... berserker

---

### Post by tjeremiah on 2009-07-20
followed instructions, updated, and everything is back to normal :)

---

### Post by dagrump on 2009-07-20
...and there goes Tokyo ..gdm BESRSERKER...

So sorry, tripped a switch. (as I search for B.O.C.)

Well, I'll perch my tail on the corner of the desk, to attach a wire after it's fixed. I'm leaving the cable connected this time!
Nanog , Thanks for the links to get wireless working, but , I'll risk the corner of the desk.

---

### Post by Slug71 on 2009-07-21
I would actually use 

```
sudo apt-get update

sudo aptitude safe-upgrade
```

instead of

```
sudo apt-get update

sudo apt-get upgrade
```

---

