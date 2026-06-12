---
title: "windows 7 theme"
date: 2014-10-10
forum: Installation &amp; Upgrades
---

### Post by grumpy_old_man on 2014-10-10
Following installation of ubuntu 14.0 I have tried to install windows 7 theme.  Following a workshop in my computer magazine I have installed the Xubuntu XFCE desktop using the following in Terminal [COLOR=#ff0000]sudo apt-get install xubuntu-desktop[/COLOR].  I have now got the 'windows' desktop with task bar at bottom of screen.

I have then entered the following commands:
[COLOR=#ff0000]sudo add-apt-repository ppa:upubuntu-com/gtk3

[/COLOR]followed by
[COLOR=#ff0000]sudo apt-get update

[/COLOR]followed by
[COLOR=#ff0000]sudo apt-get install win2-7

[/COLOR]this command has failed and I get error message 'unable to find package'.  Can any advise if the windows 7 theme is no longer available?  When entering the 'update' command some files were not downloaded or old versions were used.

Thank you

gom

---

### Post by qamelian on 2014-10-10
The problem seems to be that the3 PPA doesn't contain any builds for the version of Ubuntu.Xubuntu you have installed. The most re3cent version supported in the PPA is 13.04 (Raring Ringtail).

---

### Post by Rob Sayer on 2014-10-11
That's one reason I won't use 3rd party ppas for anything like themes/skins.  Go into synaptic (install it if you don't have it), look in sources, delete that ppa.

That stuff doesn't work anyway.  You may be able to make linux look like windows but it won't *work* like windows.  Thank God ...

And in the future be very careful about installing from external untrusted ppa's.  I'll only use them if there is no other way to do what I need to do.

---

### Post by Vladlenin5000 on 2014-10-11
> **Rob Sayer said:**
> That stuff doesn't work anyway.  You may be able to make linux look like windows but it won't *work* like windows.

+1

> Thank God ...
No, thank Linus.

---

