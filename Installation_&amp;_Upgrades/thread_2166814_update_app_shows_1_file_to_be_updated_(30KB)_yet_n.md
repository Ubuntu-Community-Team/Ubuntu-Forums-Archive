---
title: "update app shows 1 file to be updated (30KB) yet none appear in list"
date: 2013-08-11
forum: Installation &amp; Upgrades
---

### Post by neekos on 2013-08-11
greetings!
the update app in ubuntu 13.04 64bit is showing here that there is one file to be downloaded and installed (30KB) and yet when i click 'show updates' the list is empty..
any idea why that is and what to do? 
thanks

---

### Post by ibjsb4 on 2013-08-11
[Try it in terminal.]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal")

```
sudo apt-get update
```

and then upgrade

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by neekos on 2013-08-11
ah ok, that got it, yes. so there is a bug with the update gui?

---

### Post by ibjsb4 on 2013-08-11
IMO the update manager has always been buggy :)

I have been using [Synaptic Package Manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9") instead of the update manager or software center.  Again IMO, its faster and much more dependable.

Want to try it out?

```
sudo apt-get install synaptic
```

---

### Post by neekos on 2013-08-11
i do have synaptic already installed and have used it previously, though i had not thought to use it as a general upgrader - only for locating packages to install.
i just ran it and... dun dun daa... it crashed.. repeatedly.

i see segfaults in the kernel log for synaptic:
 
segfault at 8 ip 00007f51418f8aad sp 00007fff2cbb50f0 error 4 in libgtk-3.so.0.600.4[7f51417f4000+4ab000]

---

### Post by ibjsb4 on 2013-08-11
Open a terminal and try:

```
synaptic

or

sudo synaptic
```

---

### Post by neekos on 2013-08-11
aha, ok, that has resolved the issue. certainly some bizarre bugs exist in this distro!

---

### Post by ibjsb4 on 2013-08-11
One reason I go with an LTS release :)

Don't forget to mark your thread solved.

---

### Post by neekos on 2013-08-11
ah yes, ok, thanks for helping. :)

---

### Post by ricardisimo on 2013-08-11
I believe gnome-screenshot is the culprit. It appears in synaptic, but gives no name and no details in Software Updater.

---

