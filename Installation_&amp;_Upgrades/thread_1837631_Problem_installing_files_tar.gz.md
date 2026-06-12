---
title: "Problem installing files tar.gz"
date: 2011-09-02
forum: Installation &amp; Upgrades
---

### Post by SBMN7 on 2011-09-02
I recently download qemu-0.15.0.tar.gz but i can not install it on ubuntu 11.04. Please help me. How can i install it on my ubuntu. I already download it. Help

---

### Post by MG&amp;TL on 2011-09-02
I believe several forms of Qemu are available from the software centre, although I'm not sure on this. Apt-get or software centre is much preferred to a .tar.gz

If you can only get it from a tarball, right-click on it, and select 'open with archive manager', then extract it to a place you want it using the Extract button.

Then navigate to the extracted Qemu and read the README file almost always supplied with instructions on how to install, typically this will use the terminal.

If there is no readme, but 'configure' and 'makefile' files in the extracted Qemu:

```
cd <Qemu directory>
./configure
make
sudo make install
```Which is the typical way of building .tar.gz packages.

As i said, check software  centre, then synaptic or apt-get, then the web for a .deb file (these you can just double-click on), and if nothing else is around, you will have to resort to  source tarball (.tar.gz)

Hope it  helps. If you have problems, report back. :D

Although you might be better off with VirtualBox, which IS in the software centre.

---

