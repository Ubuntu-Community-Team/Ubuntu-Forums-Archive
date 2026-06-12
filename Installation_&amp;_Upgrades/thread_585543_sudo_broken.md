---
title: "sudo broken??"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by zx80user on 2007-10-21
I have loaded 7.10 on to a completely new machine and the restored the other half's home directory from a tape backup. She is also the sudo user.

Now sudo appears to have quite suddenly broken. As you might imagine this makes the machine all but impossible to administer - especially as I hadn't created a root user on it.

Now when sudo is used I get prompted for the password but nothing happens - eg I can run synaptic as an ordinary user (though it is pretty useless) but when I type sudo synaptic nothing happens - I just get the prompt.

What on Earth is going on?

---

### Post by hal8000 on 2007-10-21
Try this:
sudo passwd

(enter your password) then a new root password, this way you can do
su  (enter new root password) and continue as root

alternatively boot with the live cd, mount your root gutsy partition and
edit the sudoers list manually

---

### Post by zx80user on 2007-10-21
The first doesn't work. I'll try the CD

---

### Post by zx80user on 2007-10-21
Booting with the live CD, mounting the /dev/sda1 volume and then editing the sudoers file worked, so thanks for the tip.

---

