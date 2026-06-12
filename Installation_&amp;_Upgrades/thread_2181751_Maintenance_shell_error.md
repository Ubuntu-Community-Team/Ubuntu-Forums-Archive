---
title: "Maintenance shell error"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by TimEnid on 2013-10-18
So I just upgraded and the pc did not reboot on its own. So I had to restart it. I waited a while before doing so. So I boot back up and I get a screen that says "filesystem check our mount failed. A maintenance shell will now be started." I let this sit for a while hoping something would happen. But nothing. Any suggestions? I am unable to type anything on the screen. 
[IMG]http://i39.tinypic.com/2lmkxza.jpg[/IMG]

---

### Post by heir4c on 2013-10-19
Type after the root'prompt': 
fsck -f
If that not help disconnect the HD and plug in back. And boot up again.
Maybe a bad HD?
The system has difficulty mounting the drive.

---

