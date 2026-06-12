---
title: "icauth error when changing user id"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by Elaztic on 2010-10-20
edit:

Sometimes the solution is simple:
create the faulty account and create a new one with the desired settings ;)

----

Hi all.

Hope someone can help - perhaps the answer is very simple.

My wife just bought a new HP laptop and ofcourse the first thing to do is erase windows and install Ubuntu (10.10).
Install was perfect and very easy and I created just one account with encrypted home dir.

We have a NAS (ReadyNAS Duo) which I have set up with NFS.

My challange is that the default uid on the laptop account is 1000 and that corresponds to a different user on the NAS.
I created another admin account on the laptop and changed the uid of my wife's user to 1020.
Now if I login as my wife I get a ICauth error and it does not start up.
If I change the uid back to 1000 everything works perfect.

The other account I created does not have an encrypted home dir and changing uid for that account does not give the error.

Would prefer just to have one account on the laptop. Is it at all possible to change the uid or does that conflict because the first account you create have to have uid 1000 or because the home dir is encrypted or something completely different?

To all users (and Ubuntu): Thanks a lot for a great forum.

---

