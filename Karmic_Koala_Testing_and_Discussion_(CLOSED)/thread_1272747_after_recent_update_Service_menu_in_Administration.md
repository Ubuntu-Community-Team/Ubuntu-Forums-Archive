---
title: "after recent update Service menu in Administration disappeared"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cororok on 2009-09-22
with this menu I could turn off some services I don't need.

but now I can't see that.

---

### Post by mc4man on 2009-09-22
I just did a full update and it's still there. ( had to do 1 update manually - software store, and remove amarok2 for the time being.

Maybe ck and see if it's listed but not enabled, in ternimal

```
alacarte
```

or try to run directly

Alt+F2 and enter

```
gnome-session-properties

```

---

### Post by cororok on 2009-09-22
I've check out "Main Menu" in Preference. but "Service" doesn't exist in menu items.

"Startup Applications" is still in Preference but "Services" in Administration isn't.

---

### Post by VMC on 2009-09-22
Your right, it is gone - but not forgotten.

Tried to find it via alacarte. Not there either.

---

### Post by kansasnoob on 2009-09-22
Yep, gone! Hadn't noticed.

---

### Post by mc4man on 2009-09-22
sorry, misread what you were looking for, and was a bit distracted by the apparent partial re-emergence of automounting of cd's/dvd's issue

---

### Post by mc4man on 2009-09-22
from todays update of gnome-system-tools
 > * Disable services-admin - it is not very useful in the Upstart world
    (LP: #433701).

---

### Post by khughitt on 2009-09-23
> **mc4man said:**
> from todays update of gnome-system-tools

I saw that, too. I normally would use the services application to manage what services start-up automatically. Anyone know what people are supposed to use in the absence of services-admin?

---

### Post by ktraub on 2009-09-24
I'd like the answer to that last question too...

---

### Post by MacUntu on 2009-09-24
I'm not sure if that's how it should be done but if I don't want a service to start, I rename the 'whatever.conf' file in /etc/init/ to just 'whatever'. Without the extension it's no valid job and doesn't get started.

---

### Post by Mr. Picklesworth on 2009-09-24
[SIZE="3"]Edit: Ah, I think I understand now. It's *really* changed. Ignore me :)[/SIZE]

[SIZE="1"]> **mc4man said:**
> from todays update of gnome-system-tools

Wow, that is just absurd. "It's not useful, so we're going to scrap not only the menu item, but the entire program!" (You can't run services admin directly, either; Bash tells you to install the package it used to come in but no longer does).

I, for one, have needed services admin on numerous occasions to deal with poor packaging which installs system-wide services for minor applications. Upstart is great and all, but the boot process is NOT my primary concern when disabling unused services.
One of the more important concerns, for example, is security. If I am not going to maintain or configure a major background service like Zope (since I don't actually use it; Gaphor uses a small component it ships with), it would be a bad idea to leave that open with the possible avenues of attack it brings along.

Granted, the Gaphpor / Zope example was fixed in Karmic (Kudos for that!), but there are undoubtedly many examples.[/SIZE]

---

### Post by khughitt on 2009-10-09
*bump*

Anyone know an easy way to control which services start up with the system in Karmic?

---

### Post by Amaranth on 2009-10-09
The only way to do so is to rename /etc/init/whatever.conf to /etc/init/whatever.conf-disabled since the GUI was designed for sysvinit and we have an upstart native boot now.

---

### Post by dxxvi on 2009-10-09
In Jaunty, I saw the Service item in System | Administration to disable/enable some services at startup. Where is it in Karmic? (or did I remove some package that has it?)

Thank you.

---

### Post by Sashin on 2009-10-09
System-->Administration-->Start up applications

---

### Post by Sashin on 2009-10-09
*System -->preferences -->startup applications

---

### Post by iruel on 2009-10-09
it's different...startup applications are an application which started just after xsplash/gdm has been started(load xorg phase). but if service,it's at usplash running(booting phase).
at jaunty, its on System > Administration > Service

---

### Post by psyke83 on 2009-10-09
It's not included anymore, because it would no longer function as you expect. Karmic's startup scripts have transitioned from sysvinit (emulated via upstart) to upstart (native upstart). The Services application was designed to change the state of sysvinit scripts, I think.

---

### Post by wnelson on 2009-10-10
Just use sysv-rc-conf to start or stop services.

---

### Post by hikaricore on 2009-10-10
> **wnelson said:**
> Just use sysv-rc-conf to start or stop services.

You may not be aware of this but sysv-rc-conf no longer works for most services, and unless
modified to the new upstart system will no longer work for ANY services in the near future.
You probably should have read this thread before replying without outdated knowledge.

---

### Post by emarkay on 2009-10-10
Agreed, Bug filed:
[https://bugs.launchpad.net/ubuntu/+bug/448028](https://bugs.launchpad.net/ubuntu/+bug/448028)

---

### Post by emarkay on 2009-10-10
Addressed in this thread:
[http://ubuntuforums.org/showthread.php?p=8082506#](http://ubuntuforums.org/showthread.php?p=8082506#)
OP please mark thread as "Solved". Thanks.

---

### Post by Sophont on 2009-10-11
> **emarkay said:**
> Addressed in this thread:
[http://ubuntuforums.org/showthread.php?p=8082506#](http://ubuntuforums.org/showthread.php?p=8082506#)
OP please mark thread as "Solved". Thanks.

That thread is this thread. :-)

---

### Post by cotfessi on 2009-10-14
I'm not a hardcore command line guy and i use the DESKTOP edition of ubuntu and would expect some graphical way to manage services... even if they've transitioned the way the various services load and the old tool doesn't work, shouldn't they spend some time to develop a new UI to manage the new system???  

:mad::mad::mad:

so how do i go about managing services now??  when i google it, i get tons of articles concerning system > administration > services tool....

---

### Post by khughitt on 2009-10-15
> OP please mark thread as "Solved". Thanks.

So what is the solution?

---

### Post by johns996 on 2009-10-22
> **Amaranth said:**
> The only way to do so is to rename /etc/init/whatever.conf to /etc/init/whatever.conf-disabled since the GUI was designed for sysvinit and we have an upstart native boot now.

This method did not work when I tried to remove the avahi-daemon and its annoying as hell "network discovery service" message.  I changed the avahi-daemon.conf file stored in /etc/init as described but the message still popped up.  Is there something else that needs to be done to fully disable one of these services?

---

### Post by iruel on 2009-10-24
> **pwnedd said:**
> So what is the solution?


you could use **bum**, and you could download with command **sudo apt-get instal bum**,
or you could open from **Ubuntu Software Center** and type **Boot-up manager** in search field

---

### Post by Amaranth on 2009-10-24
Have you tried? Last time I checked it only worked with sysvinit as well.

---

### Post by iruel on 2009-10-25
> **Amaranth said:**
> Have you tried? Last time I checked it only worked with sysvinit as well.
yes,i was install it last night,after RC-version available..

---

