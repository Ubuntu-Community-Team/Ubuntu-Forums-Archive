---
title: "help, screwed up my /home folder"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by morbrakai on 2006-08-24
I was trying to install another HD as my /home folder

I mounted the HD in a temp location, and copied the /home folder over to that HD, then mounted it as /home

I mounted it manually to check it out and everything looks good, but when i reboot it wont work.

I noticed that when i cat /etc/mtab the line for the /home looks like this:

/dev/hdb1 /home reiserfs rw,noexec,nosuid,nodev 0 0

where did the noexec,nosuid,nodev come from?  wasnt in my fstab.

what should the chmod and chown be fore the /home directory and the user directories in /home?

thanks for any help

---

### Post by adds2one on 2006-08-24
Can you post your /etc/fstab?

---

