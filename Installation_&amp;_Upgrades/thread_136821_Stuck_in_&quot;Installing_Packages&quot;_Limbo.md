---
title: "Stuck in &quot;Installing Packages&quot; Limbo"
date: 2006-02-26
forum: Installation &amp; Upgrades
---

### Post by jelyon on 2006-02-26
This is an OldWorld G3, running Edubuntu (despite having downloaded what I thought was Ubuntu one time, and Kubuntu another.)

I have been through the initial install, past the point when it ejects the CD and reboots.

Upon reboot, it begins "Installing Packages."

At 5%, it fails (unmet dependencies in mysql)

It loads the GUI login

I choose shutdown, cycle the power, the box boots into OS 9.2, loads BootX, boots into Linux, loads GUI login.

I login with the user accout, and it begins loading (Window Mgr, etc.)

It kicks back out to "Installing Packages."

Again, fails at 5%. Mysql. Again.

I press escape, and it brings up the GUI login. I wait....

And it returns to "Installing Packages."

I'm almost crazy insane enraged. How the hell to I *stop* "Installing Packages" or, alternatively, get past the mysql dependencies?

(And, an unrelated question, how did I manage, despite my best efforts, to download Edubuntu *twice*?)

Thanks so much!

---

### Post by handy on 2006-02-27
All the help I can offer is to give you a **bump** I'm sorry... :confused: 

All the best!

---

### Post by wrtrdood on 2006-02-27
Not sure about the G3 but the normal console level will use one of the consoles for the log display.  Try flipping through the consoles (ALT F1-F4 on PC-101 KB) to see what else might be wrong.  You might even be able to login at that point and take a look a the logs under /var/log to do a bit more digging...

---

### Post by jelyon on 2006-02-27
It works the same way on the G3.

Here's what I see each time it fails:

[INDENT]The following packages have unmet dependencies:

mysql-common: conflicts: mysql-common-4.1 but 4.1.12-1ubunt3.1 is installed
mysql-common-4.1: conflicts: mysql-common but 4.0.24.10ubunt2 is to be installed[/INDENT]

I'm not an expert by a long shot, but that suggest to me that the package installation process is trying to install/update with *older* packages the *newer* packages that are already installed on the box.

How do I move past this? It's been a frustrating two days.

---

### Post by jelyon on 2006-02-27
As if by magic, I powered the box on this afternoon, and it loaded KDE, without the subsequent dump to the package installer. Yay!

I suspect that had I rebooted last night after a "sudo apt-get -f install" that it would have resolved the issue.

Or maybe it *was* that ream of paper I sacrificed to the Egyptian Goddess of Networking. That's Osi, of course!

Thanks to all for the help/commiseration.

---

### Post by jelyon on 2006-02-28
So it's back.

This seems to me to be a bug. Has there been anyone else stupid enough to install Ubunto Breezy Badger 5.1 on an OldWorld Mac, and willing to share their experience?

---

