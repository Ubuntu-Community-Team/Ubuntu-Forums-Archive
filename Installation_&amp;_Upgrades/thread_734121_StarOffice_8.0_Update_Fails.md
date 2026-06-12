---
title: "StarOffice 8.0 Update Fails"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by RMOP on 2008-03-24
After downloading the .jar download file (**120184-12.jar**), I ran the setup file as directed ( ./setup) and the following messages were reported:

Searching for the staroffice installation ...

read: 26: Illegal option -n

[: 28: ==: unexpected operator

The installation of StarOffice was easy (thanks to posts in this forum), but the update is a no-go. One other post has documented the same problem.

Has anyone successfully done this upgrade?

Thanks.

---

### Post by RMOP on 2008-03-24
And, here is the answer, derived from brazen experimentation:
[B]
sudo alien -i --scripts /your own directory where you put your patch/120184-12/rpms/8.rpm[/B]

That wasn't elegant, but it worked, and StarOffice reported thereafter to be happily up-to-date.

Now that I've done it, it makes sense. But trying to run setup was not going to work.

Cheers!

---

### Post by Noobdaemon on 2008-03-31
When I do that i get the following error message:

File "/tmp/120184-12/RMPS/8.rpm" not found.


What do I do?

---

### Post by ap0110 on 2008-04-06
I think RMOP means

sudo alien -i --scripts /your own directory where you put your patch/120184-12/rpms/*.rpm

so * instead of 8,

Update:
I Just ran this and it did update my SO install.
Since this script is using the wild card I would delete the language packs you don't need from the RPMS folder as it will install everything there.

---

