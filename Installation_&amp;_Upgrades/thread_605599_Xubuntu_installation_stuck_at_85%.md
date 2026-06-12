---
title: "Xubuntu installation stuck at 85%"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by dotsi on 2007-11-07
Hello,

I'm trying to do a fresh install of Xubuntu on an IBM ThinkPad 600E with 400MHz CPU, 128MB RAM and 20GB HDD. I downloaded and burned the alternate install CD and started the install with the following parameters:

```
acpi=force pci=noacpi vga=0x371
```

(as instructed somewhere)

The installation goes (well, almost) flawlessly to a point where it says "installed update-notifier" and the progress bar is at 85%. That's where it stays forever. After the first try I did a defect check on the install CD and it was OK. Also the MD5sum of the ISO image is correct.

Anything I could try next?

**EDIT:** I'm currently trying Ubuntu install from alternative CD. Same thing happends, it's frozen at 85% but this time it says "installed tomboy".

**EDIT #2:** OK, I checked the syslog on another terminal while the installation is stuck. It seems that the hang-up has something to do with the installation's inability to resolve the repository servers' addresses. How do I fix this?

**EDIT #3:** FIXED! :D On the other terminal, I ran eth0 down and then up again (with ifconfig eth0 down and ifconfig eth0 up) and now it works.

---

### Post by legendri on 2007-11-27
Thanks for your monologue and for EDIT #3  :)

---

### Post by neonpill on 2008-01-21
Echoing the thanks by legendri - I am testing the Gutsy Xubuntu ISO on virtualbox, and was starting to get worried. Cheers!

---

