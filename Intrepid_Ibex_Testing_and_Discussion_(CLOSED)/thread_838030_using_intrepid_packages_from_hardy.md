---
title: "using intrepid packages from hardy"
date: 2008-06-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by leobard on 2008-06-23
I upgraded to hardy (8.04) and would want to use one package from intrepid (8.08), namely encfs, as it has a feature I need only in the 1.4 version:
[http://packages.ubuntu.com/intrepid/encfs](http://packages.ubuntu.com/intrepid/encfs)

so - I couldn't find "newbie-compatible" documentation about how to sneak in **one package from a newer release**.

The information in the wiki does not tackle this problem, but if you help me, I could add it here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

I DO NOT want to switch to 8.08 as I am a very conservative person, fearing that switching too often will screw things up, so please don't suggest me anything along these lines of "you have to upgrade..." - I want to install one package.

---

### Post by bapoumba on 2008-06-23
The only way is to have the package backported to hardy or compile it. You cannot install it as it is, due to dependencies problems (different versions).

---

### Post by leobard on 2008-06-23
ok, so I'll try to compile it, interested to see what happens...

---

### Post by bapoumba on 2008-06-24
> **leobard said:**
> ok, so I'll try to compile it, interested to see what happens...

Yes, please post the result :)
I may not be able to help you if you have problems with compiling the thing, but others will (make sure you have build-essential installed).
[uhelp]community/CompilingSoftware[/uhelp]

---

### Post by leobard on 2008-06-25
> **bapoumba said:**
> Yes, please post the result :)
I may not be able to help you if you have problems with compiling the thing, but others will (make sure you have build-essential installed).
[uhelp]community/CompilingSoftware[/uhelp]

a ?nix-savvy friend of mine helped me, we just wget the deb package from intrepid repository, and installed it using the apt.../debian installer. Sadly, I forgot to write down the commands.
For this package, the needed dependencies were not too many and it didn't need to update any of the core things as c++ compiler.

---

### Post by bubba_169 on 2008-06-25
Might be a long shot but can't you just download the deb package from packages.ubuntu.com in the link you gave and try installing?

---

