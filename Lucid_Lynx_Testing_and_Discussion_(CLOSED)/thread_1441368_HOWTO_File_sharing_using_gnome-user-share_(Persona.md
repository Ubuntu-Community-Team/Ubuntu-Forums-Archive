---
title: "HOWTO: File sharing using gnome-user-share (Personal File Sharing)"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by linuxman94 on 2010-03-28
So as most of you have found out, if you go to System -> Preferences -> Personal File Sharing it will not let you enable network file sharing.  The window tells you that it can't be enabled because the required packages are not installed on your system and it doesn't give you an option to install them.  Well there is a very simple fix.  

Open a terminal (Applications -> Accesories -> Terminal) and copy&paste this command into it.

```
sudo apt-get install apache2.2-bin libapache2-mod-dnssd
```

This will install the neccesary packages for network file sharing.  Now if you go to Personal File Sharing, the dialog box will give you the option to enable network file sharing.  

Cheers,

Evan

---

### Post by Canis familiaris on 2010-03-31
OK this may sound noobish. But how do I access those shared files? I know files are to be kept in ~/Public. And I assume we have to share files by [http://IP](http://IP) but then?

---

### Post by PengytheDuckwin on 2010-04-04
> **Canis familiaris said:**
> OK this may sound noobish. But how do I access those shared files? I know files are to be kept in ~/Public. And I assume we have to share files by [http://IP](http://IP) but then?
You can go to the "network" bookmark in nautilus, and it should say something along the lines of "USER's public files on COMPUTER".
\


I do have a problem, though, whenever I try to access the public files on my netbook, I get the error "DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)"

---

### Post by santims on 2010-04-15
This has worked well until i restarted the next day.  i had all of my computers off, turned them all on, and then i couldn't find one single share.  I went to 'network' from my ubuntu drop down and i couldn't even see the share that should have been created from the computer that was sharing the files.

how do you get sharing to start up once you restart?

---

