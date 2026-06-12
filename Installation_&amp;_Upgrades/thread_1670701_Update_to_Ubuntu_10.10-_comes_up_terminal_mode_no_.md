---
title: "Update to Ubuntu 10.10- comes up terminal mode no desktop"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by David Crockett on 2011-01-19
HI all,

I have just upgraded my IBM desktop to Ubuntu 10.10 form 10.04 (which by the way worked well). After the update it boots up into the terminal mode.   What gives and how do I  exit it and get into the deskop.   

BTW I also updeated a 10 year old laptop and there are no problems.  I am using it right now.

Regards,
DC

---

### Post by David Crockett on 2011-01-19
I have been told that I needed to remove the proprietary driver for the nVidia card that I have installed on the computer.   Using the Ubuntu manual I have tried the following:




After  I reboot and  I login

sudo cd /etc/X11

it asks for my sudo password--I give it; but  I get the following error message:

cd: command not found. 

What's wrong.

DC

---

### Post by 3602 on 2011-01-19
don't sudo, just cd.
Or try sudo -s first.

---

