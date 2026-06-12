---
title: "im having problems installing programs"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by nonarky on 2005-10-18
yes im new to ubuntu, there some programs that i downloaded to my desktop like yahoo messenger, and the multimedia codecs, when i type in the command to install the y messenger to install it(its a deb file), i get this message:

root@c-67-185-186-221:/home/nonarky #  sudo dpkg -i ymessenger_1.0.4_1_i386.deb
dpkg: error processing ymessenger_1.0.4_1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ymessenger_1.0.4_1_i386.deb
root@c-67-185-186-221:/home/nonarky #

and i also try the other command dpkg -i ymessenger_1.0.4_1_i386.deb
and still get that same message as above, and its same same when i tryto install rpm packages,

can you tell me what im doing wrong?

---

### Post by john_c on 2005-10-18
If it has been downloaded to the Desktop then you need to give it that path.  Eg.

sudo dpkg -i /home/user/Desktop/name_of_file_to_install.deb

remember to use the capital D for Desktop,

Good luck,

John_c

---

### Post by nonarky on 2005-10-18
[QUOTE=john_c]If it has been downloaded to the Desktop then you need to give it that path.  Eg.

sudo dpkg -i /home/user/Desktop/name_of_file_to_install.deb

remember to use the capital D for Desktop,

Good luck,

John_c[/QUOTE]


for some reason i still get that message

---

### Post by nonarky on 2005-10-18
wait thanks, it works now

---

### Post by aysiu on 2005-10-18
Is it, in fact, downloaded to your desktop or not?

---

