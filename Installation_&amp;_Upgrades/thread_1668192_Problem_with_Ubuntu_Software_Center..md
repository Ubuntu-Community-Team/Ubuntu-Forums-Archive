---
title: "Problem with Ubuntu Software Center."
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by mr.johnbrug on 2011-01-16
Whenever i go into Ubuntu software center, find somthing i want, and try and click the install button, it won't do anything. I don't know what to do. If anyone could help, that would be cool. Thanks!

---

### Post by thenickrulz on 2011-01-16
Never seen this problem... does an error come up?? if there is no error im not sure why it doesn't work.. i can't really help u.

---

### Post by mr.johnbrug on 2011-01-16
Nope, no error, just no change what so ever. It worked before, but all of a sudden soon after i updated to 10.4 it didn't work.

---

### Post by Rubi1200 on 2011-01-16
Hi,
close all instances of Software Center or other package managers.

Go to Applications > Accessories > Terminal and run the following commands:

```
sudo dpkg --configure -a

sudo apt-get update && sudo apt-get upgrade
```

If there are errors reported, post them here please.

Hopefully, this should fix things and allow you to use the Software Center again.

---

### Post by thenickrulz on 2011-01-16
Check for updates that might be the problem if u have no updates i am not sure what....:confused:

---

### Post by mr.johnbrug on 2011-01-16
> **Rubi1200 said:**
> Hi,
close all instances of Software Center or other package managers.

Go to Applications > Accessories > Terminal and run the following commands:

```
sudo dpkg --configure -a

sudo apt-get update && sudo apt-get upgrade
```

If there are errors reported, post them here please.

Hopefully, this should fix things and allow you to use the Software Center again.

When i typed this into terminal, at the end of the process, it said 0 updated, and 0 for everything else and when i tried to download something, it had not worked for software center.

---

### Post by thenickrulz on 2011-01-16
Did u got into system administration update manager and check for updates if u have updates get them (If u can)!

---

### Post by mr.johnbrug on 2011-01-16
Yep, checked that, and i have no new updates needed to be installed. :confused:

---

### Post by TNT1 on 2011-01-16
Try and install the package you want from the terminal and see if it does work, then we can see if the problem is with apt or with the USC frontend.

---

### Post by mr.johnbrug on 2011-01-16
The only problem is i don't know how to find the package online for Ubuntu only something called "OpenSuSE" and "RedHat Advanced Server 4".

---

### Post by Rubi1200 on 2011-01-16
It would really help if you told us the name of the package you want to install.

Another question, check in Synaptic and see if the ubuntu-desktop package is installed.

---

### Post by ptrinder64 on 2011-01-16
Is it asking for your administrative password?

---

### Post by thenickrulz on 2011-01-16
Sry can't help you never heard of this problem??:(

---

### Post by ptrinder64 on 2011-01-17
Just a quick question - are you running this off of battery power? If so, according to [this thread]("http://ubuntuforums.org/showthread.php?t=1570696") on some netbooks you need to be plugged into mains power. My laptop seems to install ok on battery power, but that may just be a quirk.

If this isn't the issue, it may be worth trying one or two suggestions in [http://www.ubuntux.org/node/9157](http://www.ubuntux.org/node/9157). If one does work, post back the solution for future users ;),

---

