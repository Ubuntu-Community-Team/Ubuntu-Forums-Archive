---
title: "Update error"
date: 2006-03-24
forum: Installation &amp; Upgrades
---

### Post by Riona on 2006-03-24
Just installed Ubuntu and am trying to update the syste. I get the following error : e:dpkg was interrupted you must manually run dpkg --configure -a to correct the problem.
I assume that means in terminal mode? 
I brought up a terminal window and typed sudo dpkg --configure -a . 
It came back with the error sudo requires super user privilege.
I'm not really familar with the sudo command .
Help would be appreciated Thanks.

---

### Post by Sef on 2006-03-27
Try to update from the terminal window and see if that works or you get th same message.

sudo apt-get update

sudo apt-get upgrade

---

### Post by ohusby on 2006-03-27
Hi,

I have a similar problem with which I'd like to follow up in this thread. I received a system update yesterday with some locale-updates, but I didn't follow up the full upgrade process. It must have aborted, because now I can't do any more upgrades. I get the same error message as Riona. I have tried to execute the command 'sudo dpkg --configure -a', but it does not finish correctly. What can be wrong? Is there some reset method for this?

Regards ohusby

---

### Post by danilab on 2006-07-29
I've got the same error, please some help!

---

### Post by danilab on 2006-07-29
:D sudo dpkg --configure -a
that's it guys!!
pretty easy huh!!?

---

