---
title: "[SOLVED] What does this command mean?"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by f.ben.isaac@gmail.com on 2008-09-19
Hello,

I tried to install Ubuntu-restricted-extras through this command line

sudo apt-get install ubuntu-restricted-extras

Installation finished, i got an agreement. I tried to press <Ok>, but nothing happens. I tried everything the agreement did not go! Therefore, i clicked quit at the corner. I went to add/remove app. to install it through GUI. I keep getting the message below:

**********************************************************
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
*********************************************************
Anyhow i just fixed it. 

But still got questions!

1. Can you explain to me what this command for & what each parameter means

sudo apt-get install ubuntu-restricted-extras


2. I fixed it, by doing sudo dpkg --configure -a

However, i just did it by trial and error, can explain what does it mean

sudo dpkg --configure -a


Thanks

---

### Post by Cheesehead on 2008-09-19
The short answer to your question is that you interrupted the installation and corrupted part of your system.

Then you fixed the damage you caused.

While many can explain the exact meaning of each element of the commands you used, I refer you to the following manual pages for the authoritative explanation:

(These are command-line commands)
man sudo
man apt-get
man dpkg

---

### Post by null-cipher on 2008-09-19
I think if you run a:
```
sudo apt-get -f install ubuntu-restricted-extras
```
Might fix your problem.

(The -f parameter means the same as --fix-broken)

---

### Post by Jordanwb on 2008-09-19
Being a new guy I don't think he'd know about the man command.

---

### Post by null-cipher on 2008-09-19
> **Jordanwb said:**
> Being a new guy I don't think he'd know about the man command.

Granted, but surely this would be the best place to learn! :)

For the benefit of the poster of this thread, the man command is short for "manual" and opens the manual page for that command.

---

### Post by f.ben.isaac@gmail.com on 2008-09-19
Thanks! It Worked!

---

