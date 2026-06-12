---
title: "How to update ?"
date: 2019-06-20
forum: Installation &amp; Upgrades
---

### Post by pilatinum on 2019-06-20
I'm using Ubuntu server 18.04.2 for ARMv7
But update from ubuntu server 16 to 18.04.2 stuck.
I tried to execute command: [B]do-release-upgrade

[/B]But I'm getting this error:

[IMG]https://i.imgur.com/3Uyb1k5.png[/IMG]

**Please tell me how I could solve it.**

---

### Post by TheFu on 2019-06-21
I haven't any clue how to update an ARM system. Do they have a BIOS or EFI boot?  

On x86 systems, first ensure the system is fully patched. That is:
```
sudo apt update
sudo apt dist-upgrade

```If those run without any failures, reboot.  If there are any issues, fix those issues before doing anything else.

Now, assuming everything is working and you've rebooted, 
```
sudo do-release-upgrade
```
is the next command.  It is best to run this from the console, not over a network.

If this doesn't work, I'd backup my data, settings and a list of packages, then do a fresh install of the OS version I want, restore my data, settings, and use the list of packages to reinstall everything needed. Should take 30-45 minutes at most for the restore.

---

