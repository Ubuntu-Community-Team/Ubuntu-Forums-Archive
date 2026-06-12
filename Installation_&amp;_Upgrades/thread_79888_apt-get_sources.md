---
title: "apt-get sources"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by vwvr9 on 2005-10-21
Hi all,
I'm new to ubuntu.

I just installed Ubuntu and am trying to install apache2 bu using "sudo apt-get install apache2". The problem is that it prompts for the installation cd which i currently don't have with me. Is it possible for me to tell apt-get to grab the installation files from the online ubuntu repository instead of looking for the installation cdrom??

Thanks guys

---

### Post by heimo on 2005-10-21
Edit /etc/apt/sources.list and add # sign at the beginning of lines with "cdrom:[Ubuntu 5.10..." or something like that. Run apt-get update and try again. :) You can do this from Synaptic package manager Repositories menu too.

EDIT: To edit ;)
```
 sudo gedit /etc/apt/sources.list
```
or
```
 sudo nano /etc/apt/sources.list
```

---

### Post by stoeptegel on 2005-10-21
I *think* this is possibleby comment out the dvd part in /etc/apt/sources.list and do an apt-get update.

EDit
I was a little too late...

---

### Post by vwvr9 on 2005-10-21
Thanks guys.

It's working fine now. Superb!!

---

