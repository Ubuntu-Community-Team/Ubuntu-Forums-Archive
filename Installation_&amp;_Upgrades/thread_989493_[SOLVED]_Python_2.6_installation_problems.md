---
title: "[SOLVED] Python 2.6 installation problems"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by turner9929 on 2008-11-21
:confused:
Hey! im not sure if im posting this in the right place...sorry if its wrong :)

Im trying to install Python 2.6 into HardyHeronLTS and am having some problems. I have downloaded and unzipped the files into /usr/bin/Python-2.6 and, following the instructions in the README tried to go:

sudo ./configure

I get the following mesage:

[I]checking for --with-universal-archs... 32-bit
checking MACHDEP... linux2
checking EXTRAPLATDIR... 
checking machine type as reported by uname -m... i686
checking for --without-gcc... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.[/I]

The 'config.log' doesnt really tell me much...but then I dont really know what Im looking for.

Any ideas? im all out! but then, i am quite new to all this! :lolflag:

thanks
:guitar:

---

### Post by taurus on 2008-11-21
You need to install the build-essential package first before you can build anything from source.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by turner9929 on 2008-11-22
:) awesome! thanks

---

