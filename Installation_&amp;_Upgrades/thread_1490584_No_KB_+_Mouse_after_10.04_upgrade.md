---
title: "No KB + Mouse after 10.04 upgrade"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by mayagrafix on 2010-05-22
Updated to 10.o4 LTS and after the purple screen with Ubuntu 10.04 logo comes up, the log in screen shows but the keyboard and mouse cease to respond. So I am stuck at the log in prompt unable to input the password to continue boot up.

PC has no PS/2 connectors available, only has USB ports for USB keyboard + mouse.

Boot in recovery mode is possible, and after log in I have a command prompt available.

Thanks in advance to all the unsung heroes of Ubuntu Tech Support :KS

---

### Post by auntiestacey on 2010-05-26
I am having a similar experience in that my keyboard stopped working after upgrade, but my mouse keeps working. I can use the keyboard on the grub menu but it stops on the login screen. I can select the onscreen kbd option on the login screen to enter the password but still have no keyboard after I login. I have narrowed it down to the xorg.conf configuration by:
1) choose recovery mode on grub boot loader, then
2) choose failsafe graphics mode

This allows me to sign into my login with keyboard and mouse working, but with minimal graphics so some applications, like games, are not loading.

I still have not figured out why the conf file is failing. Any help would be appreciated.

---

### Post by mayagrafix on 2010-05-28
This must be the _slowest_ moving thread in all of Ubuntu-doom. Ya think someone, somewhere would have coughed up a fix by now... its only been a month plus since my first post with this problem (granted, I first went to Absolute beginners area, but still!).

Anyways, to wit: I too can get in to the CLI using recovery mode and furthermore I tried the STARTX command to get into the GUI thru the backdoor, but to no avail... as soon as the pretty pictures start to show the KB + mouse cease to function.

I would appreciate at least a workaround as to how install 10.10 (that would be from the CLI) without rewriting or reformatting my Linux partition supposing 10.10 is the fix to this problem.

Thanks in advance for **ANY** help.

---

### Post by Penguin Guy on 2010-05-28
> **mayagrafix said:**
> I tried the STARTX command to get into the GUI thru the backdoor, but to no avail...
[FONT="Courier New"]startx[/FONT] isn't a backdoor, it's the same command that's run at startup.

> **mayagrafix said:**
> I would appreciate at least a workaround as to how install 10.10 (that would be from the CLI) without rewriting or reformatting my Linux partition supposing 10.10 is the fix to this problem.
Updating to a new (unstable) release is unlikely to fix your problem.


I don't know how you can fix this, but your could [report a bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+filebug"), or see if it's the same as [this one]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/82368").

---

