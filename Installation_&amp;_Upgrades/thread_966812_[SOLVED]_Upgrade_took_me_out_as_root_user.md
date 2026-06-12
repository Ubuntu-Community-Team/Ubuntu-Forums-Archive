---
title: "[SOLVED] Upgrade took me out as root user"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by kierpaul on 2008-11-01
Can anyone help me here? I just upgraded to Ubuntu 8.10 and I can no longer access Synaptic Package Manager or user groups either. It is like I am no longer the root user to this computer (probably because I am not now for some reason or another). I need help and any help is greatly appreciated! Thank you ahead of time!

---

### Post by jpkotta on 2008-11-01
You were never root.  root is a special user that has total control, you were just able to execute commands as root (when you prefix them with "sudo").

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by prshah on 2008-11-01
> **kierpaul said:**
> I can no longer access Synaptic Package Manager or user groups either. 

Open a terminal, and give the command```
sudo
``` If you get an error "Cannot resolve hostname" (or words to that effect) see [this post]("http://ubuntuforums.org/showpost.php?p=4978295&postcount=4") for a solution.

Otherwise, you need to give a more detailed explanation of exactly what problem you are facing.

Synaptic will not run if another package manager command is working in the background (update-manager, aptitude, apt-get, etc).

---

### Post by davidkahn on 2008-11-01
Here's another possibility.
 
1. Take a look at /etc/sudoers and confirm that it has a line:
[INDENT]%admin ALL=(ALL) ALL
[/INDENT]This gives members of the admin group the right to run any command.
 
2. Check that you are in the admin group in /etc/group.
 
3. If you need to edit these files, you should boot the computer and select a "Recovery Mode" version of Intrepid, which will bring you to a command prompt, logged in a root.  Edit these files (sudo is not needed because you're already root), and reboot.
 
Good luck.
 
David

---

### Post by kierpaul on 2008-11-01
Thanks jpkotta. Rebooted into recovery and dropped to shell. Used ***adduser "username" admin ***command and it worked fine after rebooting. I am still wondering how it got deleted. I think I am going to get an Ubuntu Bible so I can be more proficient at these things. Thank you everyone anyways!

---

