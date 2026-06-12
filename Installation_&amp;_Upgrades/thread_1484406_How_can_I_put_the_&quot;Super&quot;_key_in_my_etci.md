---
title: "How can I put the &quot;Super&quot; key in my /etc/inputrc file?"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by focaccio on 2010-05-15
Hello,

Since I was unsuccesful in finding a good universal key-mapping tool in Ubuntu I've resorted to modifying my /etc/inputrc file since most of the shortcuts I want will be used at the command line.

I've already added a line like this [\C-m is for carriage return]:
**Control-o: "sudo bash \C-m"**

But I want to use the "Super" key instead of the Control key.

How can I find out what representations for keys are acceptable values in the inputrc file?

Thanks,
Greg

---

### Post by focaccio on 2010-05-16
Hi,

I'm using xbindkeys [a package in synaptic] to launch programs with keystrokes.  I am able to find out what keystroke it takes for its config file by running **xbindkeys -k** from the command line.  For example this is the reference code for "Super"+a keys:
    m:0x50 + c:38
    Mod2+Mod4 + a

The problem I have is that those codes [as far as I can tell yet] are not acceptable in the /etc/inputrc file, so I still need help figuring out how to code for the "Super" key in the inputrc file.

Thanks,
Greg

---

### Post by focaccio on 2010-05-26
Any ideas out there?  Should I re-post in a different area?

Thanks,
Greg

---

