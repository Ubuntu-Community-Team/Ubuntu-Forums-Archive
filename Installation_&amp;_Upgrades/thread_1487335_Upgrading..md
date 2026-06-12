---
title: "Upgrading."
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by Cremator on 2010-05-18
I downloaded the Ubuntu 9.04 ISO and can not figure out how you upgrade with it.

I have 8.10 installed which I want to update so that I am able to connect to the internet as the version of Ubuntu I have does not support the modem I have, I need to upgrade to a version that supports the T-Mobile USB Stick 120

The machine in question DOES NOT HAVE and ethernet connection so "Going on line" is not an option and I am puzzled as to why your not able to upgrade from a CD. It wants to "Install"

Suggestions please, and ones that are not going to wipe the current system as I have lots of files that have been created.

---

### Post by Darkness Des on 2010-05-18
Well, simply put, you could download the 9.04 Alternate ISO, then run a command similar to

```
sudo mount -o loop ~/Desktop/ubuntu-9.04-alternate-i386.iso /media/cdrom0
```
and a prompt should automatically pop up asking if you wish to upgrade from that ISO.

---

### Post by Cremator on 2010-05-19
Nice one, I will note it down and try it tonight.

---

### Post by Darkness Des on 2010-05-19
Thanks. I use that all the time myself, though not for upgrading. I just use the update manager for that, but that trick will work even without an Internet connection.

---

