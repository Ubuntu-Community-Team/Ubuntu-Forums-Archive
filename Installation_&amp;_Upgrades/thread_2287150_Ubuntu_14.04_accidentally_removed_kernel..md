---
title: "Ubuntu 14.04 accidentally removed kernel."
date: 2015-07-17
forum: Installation &amp; Upgrades
---

### Post by Albert_Palenzuela on 2015-07-17
Good morning guys,

I have accidentally removed the ubuntu kernel trying to liberate space from /boot.

It starts over and over with grub mode, the problem is that I can't set the root to my partition. I've also tried to launch ubuntu-repair, but it keeps failing. 
This the pastebin received. [http://paste.ubuntu.com/11891834/](http://paste.ubuntu.com/11891834/)

Could you please help me with this?


Many thanks

---

### Post by yancek on 2015-07-17
If you don't have a kernel in your partition, you will not be able to run the system.  What does 'removed' the kernel mean?  Did you move it or delete it?  You don't seem to have any Grub files either.  I'm not sure what you mean by "I can't set the root to my partition"?  If you have deleted the kernel, there is nothing boot-repair can do to fix that, AFAIK.

---

### Post by ian-weisser on 2015-07-17
yanceck is right. You have excised a critical component of your system, one that boot repair tools cannot replace.

Use a LiveMedia to boot, mount your HDD and backup your data.
Then reinstall.

Generally, it's safer and cleaner to use the package manager to remove old kernel packages.

---

