---
title: "Cannot Run executable (application/x-executable) File"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by J3RI3L on 2010-06-28
Hi all,

I'm trying to run (with no luck) a executable (application/x-executable) file under Ubuntu 10.04 Lucid 64 Bits.

The file is N - The Way Of Ninja a game you can download [HERE]("http://www.harveycartel.org/metanet/n_v1linux.tar.gz").

[IMG]http://mail.google.com/mail/?ui=2&ik=a82d4a730a&view=att&th=129810500834fbdf&attid=0.1&disp=inline&realattid=f_gazz6isi0&zw[/IMG]

I've tried tu run it as root, using the terminal ("./" and "sh") but haven't been succesfull.

Please help me with this, I really want to run this game. (Try it BTW)

Thanks!

---

### Post by Paddy Landau on 2010-06-29
You would have downloaded a file called
n_v1linux.tar.gz

This is not a program; it's an archive.

You need to extract the archive first, which should go into a folder called
n_v1linux
(Right-click the file and select Extract Here.)

Inside that folder you will find a bunch of documentation together with a file called
n_v14

I believe that n_v14 is the file that you want to run. Ensure that it is executable (in Nautilus, right-click the file, select Properties > Permissions > Allow executing file as program).

---

### Post by J3RI3L on 2010-06-29
> **Paddy Landau said:**
> You would have downloaded a file called
n_v1linux.tar.gz

This is not a program; it's an archive.

You need to extract the archive first, which should go into a folder called
n_v1linux
(Right-click the file and select Extract Here.)

Inside that folder you will find a bunch of documentation together with a file called
n_v14

I believe that n_v14 is the file that you want to run. Ensure that it is executable (in Nautilus, right-click the file, select Properties > Permissions > Allow executing file as program).

SOrry didn mention I've donde that already, but still get this error while opening from a terminal:

"error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory"

---

### Post by Paddy Landau on 2010-06-30
> **J3RI3L said:**
> "error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory"
I'm not an expert in this at all. All I can see is that Lucid has libgtk version 2.0 installed.

It may be that the program specifically wants version 1.2, not version 2.0. Contact the program's developers and ask about it. If it is specifically looking for an old version, it will cause a problem for you.

---

