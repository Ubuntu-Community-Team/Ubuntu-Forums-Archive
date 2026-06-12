---
title: "messed up sudoers file"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by jfix on 2005-10-14
Hi, 

being fed up having to type my password every time I was using sudo, I thought it was a good idea to change the sudoers file using sudo visudo.  However, I didn't RTFM as I should have, so I put in NOPASSWORD instead of NOPASSWD, and saved.  visudo complained, understandably, but now I cannot go back and correct my mistake because:

jakob@grumpy:~$ sudo visudo
Password:
Sorry, user jakob is not allowed to execute '/usr/sbin/visudo' as root on localhost.localdomain.

I find that I cannot execute any thing with sudo anymore.  what now?  

thanks in advance.

---

### Post by TristanMike on 2005-10-14
Perhaps if you boot into "recovery console" from your grub on your system you can make the appropriate adjustments?

---

### Post by jfix on 2005-10-15
TristanMike,  thanks a lot, rebooting in the recovery console did the trick.

BTW, what I changed in order to avoid having to type in my pass phrase every time is this:  change the line

%admin ALL=(ALL) ALL

to

%admin ALL= NOPASSWD: ALL

thanks again.

---

