---
title: "/home directory question"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by patrick1314 on 2007-04-05
Hello again.

I have a question - I have tried to find an answer myself but I can't find any reference to it. I want to see if anyone else knows of the outcome before I tried it and possibly lose data...

Can two linux installations (say two separate Ubuntus) share the same /home partition? I mount my /home directory on a different partition and I was wanting to see if a second, smaller and lighter, Ubuntu installation can share the /home partition without any trouble.

Thank you!

---

### Post by heimo on 2007-04-05
I think general consensus is that it's not recommended and is likely to cause conflicts between programs' config files - user specific settings are typically stored in your home directory (hidden files/directories beginning with a dot). But you could have separate home directories and still share files between two installs, for example, if you have a separate partition for music/videos/pictures, you can mount it under your home dir in both setups (or have it mounted under /media). I recommend not sharing home dirs between two installations.

---

### Post by patrick1314 on 2007-04-05
Ah, alright, message understood. ;)
I was thinking about that too, all the config files etc. I'll give it a miss then.
Thanks!

---

### Post by ben.s on 2007-04-05
I came up with a method for doing this, but it's not what I'd consider optimal.  My "shared home" directory is mounted as /homes and I let each distribution have its own /home filesystem.  I symlink "shared" config files (like .bashrc, for example) from /homes/user/.bashrc -> /home/user/.bashrc and create a symlink called user_home in /home/user that links to /homes/user.  

It works, and it lets me control what config files are shared and which aren't.

---

