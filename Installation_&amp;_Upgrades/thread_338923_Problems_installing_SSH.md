---
title: "Problems installing SSH"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by opsoftware on 2007-01-15
Hi,

I am using the latest relese as of 11th Jan 2007 and I am tryinh to install SSH but the is a problem..

I do the following

apt-get install ssh

which returns that SSH is dpendant on another module so I....

apt-get install othermodules

which returns saying that this is also dependant on another module still so I.....

apt-get install anothermodulestill

which returns saying that the version installed is the newest version.

What do I need to do to get SSH installed??

Many thanks

Ozzie

---

### Post by Jussi Kukkonen on 2007-01-15
Could you paste the actual commands and outputs here? What you describe shouldn't really happen

---

### Post by opsoftware on 2007-01-17
Here is exactly what is being displayed:

I type:

apt-get install ssh [enter]

[I]Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed.  This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or have been moved out of incoming.

since you only requested a single operation it is extremely likely that the package is simply not installableand a bug report against that package should be filed.

The following packages have unmet dependencies.
  ssh: depends: openssh-server but it is not going to be installed E: broken packages.[/I]

If I try to insall openssh-server i get the same as above but the following difference:

[I]The following packages have unmet dependencies.
  openssh-server: depends: openssh-client ( = 1:4.2p1-7ubuntu3.1) but 1:4.3p2-5ubuntu is to be installed E: broken packages.[/I]

Can anyone shed some light on this?????

Regards,

Ozzie

---

### Post by eXisor on 2007-01-17
I did this a few days ago. You need to install openssh-server

```
sudo aptitude install openssh-server
```

This worked out-the-box. No dependency issues on Edgy.

---

### Post by Jussi Kukkonen on 2007-01-18
opsoftware, your package database has some problems (possibly unrelated to this ssh issue). Try ***apt-get install -f***.

---

### Post by jshamlet on 2007-01-24
I just installed 6.10 as a fresh install today, and I can't get the ssh server installed either. Attempting to apt-get install ssh fails, with apt get indicating that only the client is available. I also tried apt-get install openssh-server, but was told that the package doesn't exist.

Is there a problem with the open SSH package?

[edit] Updating my repositories seems to have solved the problem. I was able to do an apt-get install ssh with no problems after the update.

---

