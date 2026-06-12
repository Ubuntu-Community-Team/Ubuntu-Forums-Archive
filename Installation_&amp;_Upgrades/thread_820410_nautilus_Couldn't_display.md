---
title: "nautilus Couldn't display"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by tw3k on 2008-06-06
After some of the last updates, I didn't notice which update in particular, I've been getting "Couldn't display" errors from nautilus.

Namely, opening Places like Computer, Network and sftp servers result in the "Couldn't display" error.

---

### Post by ajgreeny on 2008-06-06
There was a nautilus update yesterday.  Perhaps that's caused the problem, though my machine runs fine still, and nautilus will display everything I've asked it to so far.  Perhaps worth trying a reinstall of nautilus, nautilus-data, and libnautilus-extension1.

If that's no help, then, I'm afraid it will need someone more clever than myself.

---

### Post by tw3k on 2008-06-06
> **ajgreeny said:**
> There was a nautilus update yesterday.  Perhaps that's caused the problem, though my machine runs fine still, and nautilus will display everything I've asked it to so far.  Perhaps worth trying a reinstall of nautilus, nautilus-data, and libnautilus-extension1.

If that's no help, then, I'm afraid it will need someone more clever than myself.

Thanks for the suggestion. I tried both a reinstallation of those three components as well as a complete removal of all nautilus components, reinstalation of nautilus and a log out/in with the same errors.

I did disable some runlevel items. Perhaps there is a dependency there.

---

### Post by javaguru on 2009-02-17
I'm experiencing the same with media files in Debian Unstable. The files are (were) correctly registered, I'm talking about .deb packages, .odt documents, .rpm files, .avi etc. These files often have a preferred application in the "open with" tab, but still give the same error.
I'll keep an eye out for a fix.

---

### Post by redroad55 on 2009-02-17
Are you running a DHCP Modem where your Ip was changed by your IP provider or power outage on modem ?

---

### Post by javaguru on 2009-02-17
now what would that have in common with a bug in nautilus ?

---

### Post by redroad55 on 2009-02-17
nautilus cannot handle computer: location
nautilus cannot handle sftp : location

you tell me ? sftp is ssh correct ? whether it is Lan or global without more Info. about your network the Ip address under dhcp is not a constant unless setup to accommodate dhcp's non static normal state ..

---

### Post by javaguru on 2009-02-17
yes i've seen the bug reports with nautilus having trouble with network locations. Mine has trouble with registered file types

---

### Post by javaguru on 2009-02-17
> **redroad55 said:**
> nautilus cannot handle computer: location
nautilus cannot handle sftp : location

you tell me ? sftp is ssh correct ? whether it is Lan or global without more Info. about your network the Ip address under dhcp is not a constant unless setup to accommodate dhcp's non static normal state ..

This looks a lot like random generated text...

---

