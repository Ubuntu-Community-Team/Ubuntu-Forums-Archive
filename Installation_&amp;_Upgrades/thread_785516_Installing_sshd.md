---
title: "Installing sshd"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by sirius56 on 2008-05-07
I'm trying to get sshd running in 8.04 Desktop.

When I do  

sudo apt-get install sshd

I get the message "Couldn't find package."   Yet I have all of the extra repositories checked.  Can someone please tell me how to load sshd?

Thank you.

---

### Post by Whiffle on 2008-05-07
try

apt-get install ssh

---

### Post by sirius56 on 2008-05-07
apt-get install ssh    worked but that is the client side.
What I needed is the server side.  I found
apt-get install openssh-server
and that seemed to work.
Thank you.

Case closed.

---

