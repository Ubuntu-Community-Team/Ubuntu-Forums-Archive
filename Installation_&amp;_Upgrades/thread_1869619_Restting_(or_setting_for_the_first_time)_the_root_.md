---
title: "Restting (or setting for the first time) the root password"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by eddyv on 2011-10-26
Trying to help a friend recover his Win7 partition and the ability to boot from Win7 because somehow Ubuntu has become the default OS.
In the process of discovery, I found out that he cannot run sudo because he does not have the root password. He does not recall creating one. I remember creating a root password every time I installed any flavor of Ubuntu. Question(s):
If he cannot remember the root password, can he reset it?
Is it possible he did not set one at install time? If so, can he put one in now? Or run sudo with a null password somehow?
Many thanks.

---

### Post by jnorthr on 2011-10-26
you can try just pressing the enter key without entry of a password  value and if he did not create a p/w then perhaps this will allow him to change it. Also just read over on another thread that you can type
sudo -i
to set/reset super user p/w but i haven't tested this myself so cannot say if it would get you out of your problem. 

My chief concern is that your friend has blitzed his entire system when installing ubuntu by doing an automatic install which partitions the ENTIRE disk again thus wiping the windows slice. If there WERE several o/s present on a system, the bootup screen should give you a menu of which ones are there so you can choose. If you are not given a choice, then you may have lost his windows slice and all it's data. Hope your friend had good backups. You DO take backups don't you ?

---

### Post by haqking on 2011-10-26
> **eddyv said:**
> Trying to help a friend recover his Win7 partition and the ability to boot from Win7 because somehow Ubuntu has become the default OS.
In the process of discovery, I found out that he cannot run sudo because he does not have the root password. He does not recall creating one. I remember creating a root password every time I installed any flavor of Ubuntu. Question(s):
If he cannot remember the root password, can he reset it?
Is it possible he did not set one at install time? If so, can he put one in now? Or run sudo with a null password somehow?
Many thanks.

sudo password is not the root password, sudo is **YOUR**(when i say your i mean the logged on users or owners password, meaning your friends) own password to gain root priveleges if in the sudo group.

And during any install of Ubuntu you have done it would not ask you for a root password as the root account is locked by default

---

