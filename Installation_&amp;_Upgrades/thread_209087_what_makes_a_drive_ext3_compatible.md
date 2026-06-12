---
title: "what makes a drive ext3 compatible"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2006-07-04
When I did my very first attempt at installing Ubuntu, I specified ext3 as my choice for filesystem.  I believe this was while Dapper Drake was still in beta and had not yet been final released.

But I noticed that when the computer was rebooted, during the text portion of the boot information, the filesystem was listed/shown as ext2 NOT ext3.

Is there some specifications that a hard drive has to meet before it can be partitioned with an ext3 filesystem ?

Thanks.

---

### Post by firetux on 2006-07-04
Ext3 is actually ext2+journaling. Its not very weird you get ext2 to show op while booting.
You could check if however with gparted.

---

