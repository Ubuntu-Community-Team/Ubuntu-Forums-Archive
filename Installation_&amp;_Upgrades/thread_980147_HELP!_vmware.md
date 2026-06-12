---
title: "HELP! vmware"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by pdtpatrick on 2008-11-12
Please look at the attachment .. it wants to look for where my C header files are and i specify it and yet it keeps spitting the same message... am i doing something wrong?

---

### Post by Ryangarve on 2008-11-12
Maybe I'm missing something but it appears that it just can't find your headers because that directory doesn't exist.  They might be stored elsewhere.  You could try this from the root directory:

sudo find . | grep (name of file) 

Hopefully you'll be able to locate it that way then you can just point the application to that directory.

---

### Post by pdtpatrick on 2008-11-12
here's the output ... maybe its in /usr/include ??

---

### Post by pdtpatrick on 2008-11-12
I ended up using alien to make a .deb package from rpm and installed it that way.. but anyway it looks like the C headers are in /usr/include --- very different from RHEL :) 

Thanks for the prompt response by the way.

---

