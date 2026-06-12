---
title: "mcopidl and aRts"
date: 2011-11-21
forum: Installation &amp; Upgrades
---

### Post by Peter2009 on 2011-11-21
Hi!

I am trying to installed a programme and I get the following error:

```
configure: error: The important program mcopidl was not found!
Please check whether you installed aRts correctly or use
--without-arts to compile without aRts support (this will remove functionality).

```

before I get to configure without that. What does this mean?

I got from [here]("http://superuser.com/questions/125248/installing-qt-headers-and-libraries"):
```
Additionally, the ./configure checks for several tools that were part of aRts -- the mcopidl and artsc-config commands, which are no longer included in any KDE packages in the standard Ubuntu repositories. aRts was an old KDE sound library, and I believe it's been completely replaced or subsumed.
```

So far I am trying to create a bash file as suggested on the same article but when I do
```
/bin$ sudo cat > mcopidl.sh
```

I get:
```
bash: mcopidl.sh: Permission denied
```

Can I not create files on the bin folder?

---

### Post by Peter2009 on 2011-11-21
I cannot get this going I have look a bit on the net and seen a possible solution was install libarts1-dev but I looked and I have installed 

libartsc0-dev_1.5.9-2_i386.deb from [here]("http://packages.debian.org/lenny/i386/libartsc0-dev/download")


libartsc0_1.5.9-2_i386.deb from [here]("http://packages.debian.org/lenny/i386/libartsc0/download")

libarts1c2a_1.5.9-2_i386.deb from [here]("http://packages.debian.org/lenny/i386/libarts1c2a/download")


But when I am going to install

libarts1-dev_1.5.9-2_i386.deb

from [here]("http://packages.debian.org/lenny/i386/libarts1-dev/download") I am getting the following error:

```
Error: Dependency is not satisfiable: libartsc0-dev (= 1.5.9-2)
```

P.D. As you have noticed they are from Debian previous version!

I am going to compile with no aRtos if anyone solve this could you please reply... Thanks

---

