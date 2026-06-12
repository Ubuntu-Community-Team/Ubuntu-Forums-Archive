---
title: "Ubuntu 20.04 grub2 won't update - package error"
date: 2023-09-30
forum: Installation &amp; Upgrades
---

### Post by Tom McD on 2023-09-30
The recent grub2 update for Ubuntu 20.04 will not update.  The following error message:

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
Transaction failed: Package dependencies cannot be resolved
 The following packages have unmet dependencies:

grub-efi-amd64-signed: Depends: grub2-common (>= 2.02+dfsg1-5) but 2.04-1ubuntu26.17 is to be installed


apt policy lists grub2-common as 2.04-1ubuntu26.17 as currently installed, and is the recommend version.

-- Tom

---

### Post by Bashing-om on 2023-09-30
Tom McD hello

Show us - between code tags - the results of terminal commands:
```

sudo apt update
sudo apt upgrade
sudo apt -f install

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

See here what tale gets told :)

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Tom McD on 2023-10-01
Thank you.   The automated software updater is what showed the failure (GUI window).
Manually going through the update / upgrade process using the CLI fixed the problem.

-- Tom

---

### Post by ajgreeny on 2023-10-01
Great news!
Please mark the thread as SOLVED in the Thread Tools menu above. It can be a great help to other users searching the forum.

---

