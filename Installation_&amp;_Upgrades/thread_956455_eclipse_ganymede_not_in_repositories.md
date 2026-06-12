---
title: "eclipse ganymede not in repositories"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by opticyclic on 2008-10-23
The existing version of eclipse in the repositories is quite old (3.2)
Who do we pester to get the latest version (3.4 - ganymede) in there?

---

### Post by jespdj on 2008-10-23
Because it's not in the repository doesn't mean you can't use it. You can just [download the .tar.gz file](http://www.eclipse.org/downloads/) and unpack it in any directory you like, for example:
```
mkdir eclipse-3.4
cd eclipse-3.4
tar xfz ~/eclipse-jee-ganymede-SR1-linux-gtk-x86_64.tar.gz
```
You could [file a bug](https://launchpad.net/ubuntu) asking to update the Eclipse package to the latest version (which is 3.4.1 at the moment).

---

### Post by dusan.saiko on 2009-04-07
Bump.

Is there any reason why Eclipse in ubuntu repositories is still held to the 3.2 version ?
If there is any technical problem (I guess there should not be any) of upgrading to newer version, I would may be suggest to remove eclipse from repository completly, rather than to keep quite old obsolete version in it.

---

### Post by opticyclic on 2009-04-07
I agree.
It wont be too long before 3.5 is released either.
Who do we pester to get 3.2 removed and 3.5 on the list of software to be added?

---

### Post by UmeshAawte on 2009-06-04
**Can I have both versions of eclipse. **

Currently I am using 3.2 and downloaded the latest version (eclipse 3.4) and did as suggested. I tried to lunch new eclipse that is 3.4 but I could not run it. It starts the 3.2.

Thanks in advance.

---

### Post by opticyclic on 2009-06-04
How did you try to start 3.4?
From the start menu or from the command line?
Since you downloaded and extracted the tarball you will have to start eclipse from that directory.
The shortcut in the menu will still point to 3.2 unless you remove it or manually change the link to point to 3.4

---

