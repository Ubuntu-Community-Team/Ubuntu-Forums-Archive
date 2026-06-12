---
title: "Can't Access Root, want to upgrade from 6.06 to 7.04"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by jrmclaugh on 2007-05-04
Hi, I installed 6.06 onto my laptop a while back, but could never get internet working because I somehow didn't have access to root with my main user account, and didn't know how to log into it. 

I'm a newbie to linux, so it may just be me not understanding something, but I had someone more knowledgeable try to help, but to no avail.  

So now I'd just like to clear out 6.06 and freshly install 7.04 properly.  Is this the best option?  If so, how do I go about it safely?  Any help is appreciate.  Thank you in advance.

- James

p.s. I'd like to keep my windows install intact (not screw up the boot loader or anything), since I finally have that the way I want it for school.  Thanks again.

---

### Post by jfinkels on 2007-05-04
> **jrmclaugh said:**
> Hi, I installed 6.06 onto my laptop a while back, but could never get internet working because I somehow didn't have access to root with my main user account, and didn't know how to log into it. 

I'm a newbie to linux, so it may just be me not understanding something, but I had someone more knowledgeable try to help, but to no avail.  

So now I'd just like to clear out 6.06 and freshly install 7.04 properly.  Is this the best option?  If so, how do I go about it safely?  Any help is appreciate.  Thank you in advance.

- James

p.s. I'd like to keep my windows install intact (not screw up the boot loader or anything), since I finally have that the way I want it for school.  Thanks again.

Sure you should have no problems reinstalling Ubuntu.

Or, you could boot into Ubuntu, then type the following in the terminal:
```

sudo aptitude update && sudo aptitude dist-upgrade

```
and hopefully that should upgrade your whole system from 6.06 to 6.10. Once that's all done, type the command again, and you should be all updated from 6.10 to 7.04.

Reinstalling may just be easier and faster :D

See here for more information on root user and "sudo".
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

And this website is excellent for new users.
[http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)

---

### Post by jrmclaugh on 2007-05-04
Wow, thanks for the fast reply.  There is another problem, however.  I don't have wired or wireless internet access working.  Is there a way to do that using the CDs?  Thanks.

- James

---

### Post by phidia on 2007-05-04
You can upgrade from a cd with synaptic or apt

> sudo apt-cdrom add insert the cdrom <enter>
then
> sudo apt-get update && sudo apt-get dist-upgrade

---

