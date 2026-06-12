---
title: "Unknown permission issue"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by DRK-AAM on 2007-08-28
Hey everyone, 

I've had a strange issue for the past couple of days... I can't upgrade any of my softwares, neither with Synaptic nor manually in terminal...

Whenever I type a command and add "sudo" as a prefix, I get the following message:

"sudo: must be setuid root"

All I know is that manually installed Java and had to chown some folders to my username, but nothing that could conflict with the root account...

So I'm stuck and I really don't feel like reinstalling Ubuntu for the !%?@th time... Help please... Really... Help!

Thanks a mil!!

---

### Post by Pumalite on 2007-08-28
sudo dpkg --remove --force-remove-<packagename>

---

### Post by DRK-AAM on 2007-08-29
Thanks,

So, I did try the command you posted, but I get the same message again: "sudo: must be setuid root"...

Any task that requires root permission isn't working at all. For instance, the root terminal app won't even load, like I said, Synaptic neither... Or another example, I open software updates, I see the available updates but as soon as I click on "Install", it just re-checks the updates and nothing happens...

I really don't know if installing Java has something to do with all of this finally... Rrrrrrr!

---

### Post by Pumalite on 2007-08-29
If you installed Java through other than Synaptic; that did it. Check the forum; there are many threads with the same complaint.

---

### Post by DRK-AAM on 2007-08-29
Ohhhh... I see... Thanks for the tip, I really appreciate it!

---

### Post by DRK-AAM on 2007-08-29
Well... I really can't do anything... All the commands or apps taht need a password to activate won't even load... I'm really on the verge of giving up... 

Note to self: don't mess with what you don't know!!
Note to self (bis): but that's how you learn!!! :P

---

### Post by merlinus on 2007-08-29
You might try this:

Find the affected command by **which sudo** or **which...** where ... is the affected command.Then:
[B]$ su
# chown root:root /usr/bin/sudo
# chmod 4111 /usr/bin/sudo[/B]
or the path to the affected command.

Or this:

become root via su or such
cd /usr/bin
chmod 4111 sudo

-merlin

---

### Post by DRK-AAM on 2007-08-30
Hey Merlinus, 

I have tried that too, but that didn't do either... I've been trying to gain root access and permission and nothing works, but I mean NOTHING... Arf... Well, thanks for the tip!!

---

