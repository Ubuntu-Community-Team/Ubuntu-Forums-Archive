---
title: "Zotac ZBOX Nano hung/boot wiped during apt upgrade"
date: 2020-02-29
forum: Installation &amp; Upgrades
---

### Post by danaroode on 2020-02-29
I have been running Ubuntu 18.04 on a Zotac ZBOX CI325 Nano for a year or so, it has been working fine.  I have previously done apt update/apt upgrade without problems.  I got a bit behind and tried to upgrade the box yesterday after about 3 months of no upgrades.  The "update" completed fine, and the "upgrade" was sailing along updating packages.  The system then hung after these commands:

[COLOR=#000000][FONT=Arial]Setting up grub-efi-amd64-signed (1.93.15+2.02-2ubuntu0.14)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Installing for x86_64-efi platform[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
I tried to reboot but I am placed into grub and haven't been able to figure out the commands to boot from there (linux to specify a kernel, then boot, but I haven't gotten the root= and other parameters right).

Evidently the update script destroyed part of my boot record.  Can anyone point me in the right direction to fix this?  I didn't expect a routine upgrade to hose my system.

Thanks,

  Dana

---

### Post by CelticWarrior on 2020-02-29
If you forced a reboot while ```
[COLOR=#000000][FONT=Arial]Setting up grub-efi-amd64-signed (1.93.15+2.02-2ubuntu0.14)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Installing for x86_64-efi platform[/FONT][/COLOR]

```
then that certainly broke it. It takes a long time, you should have waited.

First check in UEFI settings > Boot that you still have "Ubuntu" (it means Grub). If not change it back to "Ubuntu" and try again. If it's correct (meaning: whatever happened didn't mess with those settings) then you will need to reinstall Grub and hope that will be all ( a forced reboot may have corrupted other file systems).

Let's first check the obvious and then move to other solutions on the go.


> Evidently the update script destroyed part of my boot record.

No, your impatience and the forced reboot did it, not the script.

---

### Post by danaroode on 2020-02-29
Thank you for your help.  I reinstalled grub and all is well (I found boot-repair which was very helpful).  I restarted the upgrade after I got the system back up normally, it did the grub-efi-amd64-signed install again, took a few seconds, and the script finished normally.

I was not particularly impatient with the upgrade yesterday, something seems to have gone wrong, I don't know what.  I was letting the script run, wasn't watching it.  I didn't expect any changes to the active system, which hosts a private web server among other things.  I got a text that the web server stopped responding, and turned my attention the script to see it had stopped after the install of grub.  No characters were being echoed when I typed on keyboard, and there was no network response from the system.  All in all I must have waited 15 minutes before I forced a reboot.

If that command can take a long time (it did not for me when I reran it) someone might want to add a warning for clueless folks such as myself.

Thank you again for pointing me in the right direction.

  Dana

---

### Post by CelticWarrior on 2020-02-29
> **danaroode said:**
> No characters were being echoed when I typed on keyboard, and there was no network response from the system.  All in all I must have waited 15 minutes before I forced a reboot.

Previous comment about impatience retracted.
It may take along time in some entry level laptops but surely not several minutes. Something else must have happened (I have no idea) but not with the script itself.

---

