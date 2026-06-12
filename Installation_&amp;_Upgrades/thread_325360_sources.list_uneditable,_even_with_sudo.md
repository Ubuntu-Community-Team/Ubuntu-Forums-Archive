---
title: "sources.list uneditable, even with sudo"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by Nachtengel on 2006-12-25
I have found that my /etc/apt/sources.list file is unreadable and uneditable, even by using sudo.  I can't find some packages I should be able to find in synaptic, so I was going to check my repositories.  The repositories dialogue doesn't come up, only flashing on the screen before exiting out, saying that the repositories have changed and that they should be reloaded.  When I headed to the console to manually edit the /etc/apt/sources.list file, I found that I was unable to 'ls' 'more' 'cat' or 'gedit' the /etc/apt/sources.list file, even prefixing all these commands with sudo.

What can I do to regain control of my sources.list file and make the proper changes so I can upgrade and install software again?

---

### Post by Spin Doctor on 2006-12-25
Weird! Did you by accident change your system rights?

---

### Post by Nachtengel on 2006-12-25
No, I'm very sure I did not.

Though as an update, I rebooted 'cause everything was acting strangely, and my RAID array had to be rebuilt. (RAID 1. hosted the /  and /swap partitions)  That's ongoing still, so I'll post whenever that finishes.

---

### Post by riven0 on 2006-12-25
Here is a workaround you can take in the meantime.

Log out >> Go to** Sessions** >> Choose **Failsafe Terminal**. You should get a plain terminal screen with a blank background. Type **sudo -s -H **

Now edit with:
> 
nano /etc/apt/sources.list

To save the file: **CTRL + S*** or* **CTRL + ALT + X**... whichever works for you.

To get back to the login screen, type **exit** and then another **exit**.

---

