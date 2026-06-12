---
title: "How to install tar.gz file"
date: 2005-07-09
forum: Installation &amp; Upgrades
---

### Post by manc39 on 2005-07-09
How do I install Firefox?

I've tried this but it does nothing:

sudo tar -xzvf firefox-1.0.4.installer.tar.gz

cd firefox-installer
./firefox-installer

Will Firefox appear in K-menu > internet once installed?

---

### Post by alastair on 2005-07-09
That looks about right (no need for "sudo" if you do this in your home dir ofcourse).No messages at all?

If "firefox-installer" is not executable, you will have to run via :

sh firefox-installer

No idea about menu's. Are there not firefox packages around?

---

### Post by adwait on 2005-07-09
I think it does appear there.......when u run ./firefox-installer, does it run? Maybe you should change its permissions using chmod +x firefox-installer and then try again..

---

### Post by manc39 on 2005-07-09
Following the

sh firefox-installer

I get a message saying: error while loading shared libraries... libgtk-x11.. shared object file...no such file or directory

_____________________________________________________________________

also, 

firefox-installer ./configure

says; command not found

---

### Post by alastair on 2005-07-11
It would be surprising if this was not installed.

I have :

/usr/lib/libgtk-x11-2.0.so.0.600.4
/usr/lib/libgtk-x11-2.0.so.0

from package : libgtk2.0-0

---

