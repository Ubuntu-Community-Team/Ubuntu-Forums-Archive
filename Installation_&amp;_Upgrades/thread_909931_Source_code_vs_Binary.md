---
title: "Source code vs Binary"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by priestscientist on 2008-09-04
Ok look; I am still learning Linux and as far as installation. when it comes to installing a program or library; you usually install by *"./configure"[I] then [I]"make"* or *"make install"*. But when it comes to a Binary file; what the hell are you suppose to do with a binary file? It sounds like a secret and i am lost and I need help. are you suppose to compile it? Is it suppose to be used as a command once you are in the directory from terminal? I don't understand and I need help with this. And if I don't know this. this will hinder me. Please help with suggestions, links, code examples or what ever. Any help is appriceated. Thanks in advance.

---

### Post by iaculallad on 2008-09-04
> **priestscientist said:**
> Ok look; I am still learning Linux and as far as installation. when it comes to installing a program or library; you usually install by *"./configure"[I] then [I]"make"* or *"make install"*. But when it comes to a Binary file; what the hell are you suppose to do with a binary file? It sounds like a secret and i am lost and I need help. are you suppose to compile it? Is it suppose to be used as a command once you are in the directory from terminal? I don't understand and I need help with this. And if I don't know this. this will hinder me. Please help with suggestions, links, code examples or what ever. Any help is appriceated. Thanks in advance.

Source code is the programming language statements/lines of text that are created by the programmer. Binary file is the pre-compiled source code ready for deployment.

What you can do to a binary? Simple, to install it (as in deb files):

```
sudo dpkg -i filename.deb
```

---

### Post by Sef on 2008-09-04
> What you can do to a binary? Simple, to install it (as in deb files):

Code:

sudo dpkg -i filename.deb



Or with Ubuntu, just click on the deb package and it will install itself.

---

