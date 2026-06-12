---
title: "Resuming from hibernate fails because of late decryption of swap"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by megandy on 2008-01-22
Hi all,

after an upgrade of cryptsetup the order of my cryptodisks has changed. This seems to be the reason why my system fails to resume from hibernate.

I have 2 encrypted partitions (set up at installation time of ubuntu). One is the swap whereas the other my home directory. Before the recent upgrade of cryptsetup a password prompt appeared just after loading of grub (when the splash screen is shown). After entering the password the system continued loading until a prompt for my /home appeared.

After the recent upgrade to cryptsetup_1.0.5-ubuntu2.1 both prompts appears after some time of booting - just at the same point where my home-disk was decrypted.

Entering both passwords leads to the following message:

 * sdb5_crypt: the check for '/dev/mapper/sdb5_crypt' failed. /dev/mapper/sdb5_crypt contains data:  - The device /dev/mapper/sdb5_crypt contains a valid filesystem type suspend.

But the system does not resume. Has anybody an idea?

---

