---
title: "How do you uninstall programs installed using make?"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by AkuTenshi on 2008-09-20
I was wondering how one would go about uninstalling something that was installed with ./configure -> make -> make install. Makefiles don't seems to have a 'remove' section, and make does not seem to have a built in 'sudo make remove <program>' feature. Any help?

---

### Post by cariboo on 2008-09-20
CD into your source directory and run:

```
sudo make uninstall
```

Jim

---

### Post by AkuTenshi on 2008-09-20
Nope, that just gives me this error:
```
make: *** No rule to make target `uninstall'. Stop.
```

---

### Post by issih on 2008-09-20
Make is a utility that can be configured to do just about whatever the programmer wants in terms of compiling software and placing it...

practically all software provided that way comes with a readme file....that will detail the steps that you should take to install and probably uninstall the system...there is no guaranteed answer with make, it just doesn't work like that.

Hope that helps.

---

### Post by AkuTenshi on 2008-09-20
Thanks, I will try to edit the install section of the Makefile to do the opposite of what is there already.

---

