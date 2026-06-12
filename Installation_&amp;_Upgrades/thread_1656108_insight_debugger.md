---
title: "insight debugger"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by chuchi on 2010-12-30
Hello friends! I'm learning to assembly program, and the tutorial follows a debugger called "insight". I wanted to install it from ubuntu packages, but the package isn't avaliable from my "Lucid Lynx" but it's from "dapper" and others versions. Is there any problem if I install the package from other version?

---

### Post by gordintoronto on 2010-12-30
There's a later version:
[http://packages.ubuntu.com/karmic/insight](http://packages.ubuntu.com/karmic/insight) 

It has 8 dependencies, and they probably have dependencies. If you already have all (most?) of the dependencies installed, you might be able to use it.

Or you could try the insight home page:
[http://sourceware.org/insight/downloads.php](http://sourceware.org/insight/downloads.php)

---

### Post by chuchi on 2010-12-30
I have put the line "deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) karmic main universe" in my source.list file. And when I type "apt-get update" i get this error

```


"Err http://ubuntu.mirror.cambrium.nlkarmic/main Packages 403  Forbidden"


```

And I can't install it!!. Installing from the web page it's impossible to me. I have been all the afternoon trying!!!!

Many thanks!

---

### Post by gordintoronto on 2010-12-30
Get rid of the bad line in your Sources file. You can download directly from [http://packages.ubuntu.com/karmic/insight](http://packages.ubuntu.com/karmic/insight)

The "packages" site is primarily for people who have Ubuntu systems which are not connected to the Internet.

However, you need to check the dependencies manually, in Synaptic.

---

### Post by chuchi on 2011-01-03
Hello!! Now i realised gdb allow me to learn assembler!! Many thanks!!!

---

