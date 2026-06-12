---
title: "Kernel panic - not syncing - HELP"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by psycolor on 2007-11-26
Hello.
I'm trying to install Xubuntu on a old pc. The disk is empty. The version is xubuntu-7.10-alternate-i386. HD 2Gb, RAM 128MB.

Some seconds after installation is started I encounter this error:
kernel panic - not syncing
Attempted to kill init
And the system freezes.

Could you please help me to understand and solve the problem? I'd like to install Xubuntu and try this new OS.

Thanks,
psycolor

---

### Post by V-600 on 2007-11-26
I encountered a similar problem, though with a slackware install. It turned out to be a problem with the grub entry. Check to see if the root device is set correctly as this caused the error for me.

---

### Post by psycolor on 2007-11-26
Thank you for the answer. What does it mean "see if the root device is set correctly"? Do I have to check if the devices inside the pc are connected as masters to the master cable? Both Hdd and cdrom?
In fact this is an installation from zero and I have not set any root directory or similar things.
Bye.

---

