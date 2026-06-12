---
title: "Newbe installed ubuntu over internet won't boot to desktop"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by dannyj on 2008-03-13
HELP!
I installed ubuntu from the internet because the CD wouldn't read the iso disk. it starts and looks like it's going to start fine but it won't boot to the desktop. It boots to "dannyj@ubuntu:~$". How do I get it to boot to the desktop?

---

### Post by Pumalite on 2008-03-13
You might have installed the Server Edition.
Try:
sudo aptitude install ubuntu-desktop

---

### Post by dannyj on 2008-03-13
Thanks for the quick reply. I tried the sudo aptitude install ubuntu-desktop and it looked like it was going to do it but at the end it said do I want to ignore the error (which I couldn't find) or abort. I picked "Yes" -ignore the error. it looked like it was trying to download a bunch of files  but after each file it had "Error: could not resolve 'us.archive.ubuntu.com'.

Any other ideas?

---

### Post by Pumalite on 2008-03-13
Take a look at your /etc/apt/sources.list

---

### Post by dannyj on 2008-03-13
I apologize for being a newbe but I don't know how to check my /etc/apt/sources.list. Is there a way to start over the install that I started or go to an install option list of some kind? this is getting frustrating.

---

### Post by Pumalite on 2008-03-14
Read the link carefully and check the iso you pick carefully too:
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

