---
title: "Update configuration"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by adriat on 2011-05-02
Hello!
Every time I update a program, the OS... etc.  it appears to me two extra lines in the grub (a new version of the OS)
How can I change this configuration or delete the previous versions?

Thank you.

---

### Post by dino99 on 2011-05-02
by default, and its needed, each kernel insert two lines in the menuentry: if the main fail then you still can boot on recovery mode (the second entry)

and its also a good idea to have the previous kernel, at least; to be safe if the other is completly broken (this happen sometimes with video driver not fully compatible in early time)

otherwise, with synaptic you can remove/purge the kernel(s) you dont need

---

### Post by adriat on 2011-05-02
Thank you for answering, dino99

Should I leave all those versions there? will this versions disappear from the grub when I install other version of the OS (for example UBUNTU 11) ?
And, just for knowing... Are this packages (capture) ? 

Thank you.

---

