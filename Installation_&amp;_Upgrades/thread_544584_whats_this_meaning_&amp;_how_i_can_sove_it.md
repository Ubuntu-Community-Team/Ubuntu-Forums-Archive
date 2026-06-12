---
title: "whats this meaning &amp; how i can sove it?"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by hesham on 2007-09-06
some application when i make ./configure i receive this error :-

checking bzlib.h usability... no
checking bzlib.h presence... no
checking for bzlib.h... no
configure: error: libbzip2 headers and/or libraries could not be found


whats the meaning & what i can do to solve it?

---

### Post by ddrichardson on 2007-09-06
You don't have the bzlib-dev package installed. Use apt-get or synaptic to install it.

---

### Post by mxg01 on 2007-09-06
I think you are missing a Ruby package. In fact maybe all of them. Package libruby1.8 (1.8.5-4ubuntu2) should sort this out.

The package details are at:

[http://packages.ubuntu.com/feisty/libs/libruby1.8](http://packages.ubuntu.com/feisty/libs/libruby1.8)

You should be able to get it via Synaptic or apt-get.

---

### Post by ddrichardson on 2007-09-06
> **mxg01 said:**
> I think you are missing a Ruby package. In fact maybe all of them. Package libruby1.8 (1.8.5-4ubuntu2) should sort this out.

The package details are at:

[http://packages.ubuntu.com/feisty/libs/libruby1.8](http://packages.ubuntu.com/feisty/libs/libruby1.8)

You should be able to get it via Synaptic or apt-get.
Possibly, but that package doesn't contain the header files that configure is looking for.

---

### Post by mxg01 on 2007-09-06
Ah... didn't realise that the header files are not in that main Ruby package.

---

