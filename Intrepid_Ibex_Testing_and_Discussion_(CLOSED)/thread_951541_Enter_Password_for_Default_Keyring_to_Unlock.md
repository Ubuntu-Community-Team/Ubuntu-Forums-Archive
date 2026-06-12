---
title: "Enter Password for Default Keyring to Unlock"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by carusoswi on 2008-10-18
Recently, when booting into 8.10, this box pops up.  The title message includes this additional advise:

"The application 'networkmanager applet (/usr/bin/nm-applet) wants access to the default keyring, but it is locked'

So, I enter my system password, click ok, and all is well.

What is causing this message to pop up and how do I fix it?

Caruso

---

### Post by syko21 on 2008-10-18
If your wifi has a network key then the keyring will memorize it for you. But to keep it secure it requires a password to give the nm-applet (that wifi icon in the task bar) access to your network key.

---

### Post by adam on 2008-10-18
Make sure "libpam-gnome-keyring" is installed. I think you also have to use GDM to login for it to work.

---

### Post by mistadman on 2008-10-18
> **carusoswi said:**
> Recently, when booting into 8.10, this box pops up.  The title message includes this additional advise:

"The application 'networkmanager applet (/usr/bin/nm-applet) wants access to the default keyring, but it is locked'

So, I enter my system password, click ok, and all is well.

What is causing this message to pop up and how do I fix it?

Caruso



Are you using auto login? If so, see: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/137247](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/137247)

---

### Post by nanog on 2008-10-18
alt F2 seahorse
edit --> preferences
select "login keyring" change password to a "blank" password

as the warning states this is a security risk.

---

### Post by carusoswi on 2008-10-18
Thanks for the link.  I use auto login, read the Launchpad thread, am more confused than ever.  It's a but, it's not a bug, Launchpad is for bug reporting, not support, on and on.

What I know is that when I first installed the beta, this problem did not exist.  It cropped up due to upgrades, so something in development has caused it.

Hopefully, it will be fixed along the way to the LTS release.

Was just thinking to myself that with 8.10 I might be free of the annoying problems experienced in i8.04, but, perhaps I spoke to soon.

This is a minor annoyance that I can live with, but I have a hard time understanding why this bug-feature-non-feature-non-feature-whatever seems to have been deliberately introduced.

Caruso

---

### Post by carusoswi on 2008-10-20
This evening, I was busy doing other things when I turned on my computer.  To my surprise, I came back to find that Ubuntu had booted up, loaded the desktop, and had searched for the router without my having to enter a keyring password. 

Guess the inconvenience has been fixed.

Caruso

---

