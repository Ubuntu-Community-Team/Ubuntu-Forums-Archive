---
title: "Install packages without root permissions"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by cad on 2007-10-19
Hello Please tell me if there is a way to install a new package without root permissions. I just want a install a package for myself and I dont want to disturb the /usr directory. I want to install it in my own home directory. Could someone please suggest if there is a way to do so.

And also please suggest if there is a way to do it in fedora 6 too, one of my friends uses fedora!

Thanks in anticipation.

---

### Post by disasm on 2007-10-19
You could try using dpkg -x to extract the package, but then it will give you a complete root structure in your home directory, and may or may not work. My suggestion would be if you don't want the package installed system wide, to see if you can find a tarball binary, or get the source and compile it manually in your home directory.

Your only other option I can think of is have a chroot setup in your home directory. You would need root permissions to set it up, but you could run the packages from your home directory without having root access. I'm pretty sure I wouldn't suggest this one.

Sam

---

### Post by cad on 2007-10-19
Thank you very much disasm but it's not that I desire not to have anyone else use the package, the very basic problem is that I am not the root so there is nothing I can do about it. Thank you very much again and please post here if you have more such ideas and also please post if you have the answer to the related query for fedora 6

---

### Post by disasm on 2007-10-19
> **cad said:**
> Thank you very much disasm but it's not that I desire not to have anyone else use the package, the very basic problem is that I am not the root so there is nothing I can do about it. Thank you very much again and please post here if you have more such ideas and also please post if you have the answer to the related query for fedora 6

If you don't have root, your best option is to create an apps  dir in your home directory and build from source.

In general:
./configure --prefix=/home/user/apps
make
make install

Then add /home/user/apps/bin to your path in your bashrc.

This tactic will work on any linux distro, including fedora, however; I avoid fedora and anything rpm related like the plague.

Sam

---

