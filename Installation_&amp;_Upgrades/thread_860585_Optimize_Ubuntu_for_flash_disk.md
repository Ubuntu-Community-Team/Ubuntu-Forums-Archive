---
title: "Optimize Ubuntu for flash disk"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by mikaelstaldal on 2008-07-15
I have successfully installed Ubuntu onto an 4 GB USB flash disk.

However, I have noticed that Ubuntu for no apparently important reason frequently touches certain files. And that not good since a flash disk can only handle a certain number of writes.

So I want to minimize the unnecessary writes to the flash disk.

For example there are three files in /etc which are touched at least once everytime I boot: 
/etc/mtab 
/etc/resolv.conf 
/etc/adjtime
How can I make it stop doing that?

I have already mounted /tmp, /var/log and /var/tmp as tmpfs (in addition to /var/run and /var/lock which Ubuntu does by default), but I don't want to mount /etc as tmpfs because I want to keep my configuration and be able to make persistent changes to the configuration sometimes.

There also seems to be some more stuff in /var which is touched frequently.

---

