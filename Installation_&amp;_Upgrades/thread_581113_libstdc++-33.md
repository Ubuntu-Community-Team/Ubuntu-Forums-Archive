---
title: "libstdc++-33"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by several on 2007-10-19
Hello,

this is my first day with linux / ubuntu .... but i think ive still learned a lot :-)

But my actual Problem i think i couldn't manage to solve on my own...

First: Im trying to install "hamachi" for linux. The original version doesnt work,
so i foundet a solution to install the pentium version.

Then i get an error after compiling and installing:

```

hamachi: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

therefor i found a solution in the hamachi forum and it told me to do this:

```

sudo apt-get install compat-libstdc++-33

```

but then i get this error :( (translation in brackets)

```

Paketlisten werden gelesen... Fertig    (reading paketlist...done)
Abhängigkeitsbaum wird aufgebaut      (don't know)
Reading state information... Fertig       ( ... done)
E: Konnte Paket compat-libstdc++-33 nicht finden    (E: Couldn't find compat-libstdc++-33)

```

Another FAQ told me to use yum .... but if i try it, i get the message, that yum isnt installed-- and if i try to install it, i get the same message like the last one, but saying:

```

E:Couldn't find paket yum

```

I hope somebody is able to read my lousy english and knows how to fix that...

regards,
several

---

### Post by kylepip on 2007-10-19
I solved this issue by enabling all ubuntu repositories, then reloading.  Subsequently, libstdc++5 was available for install.

---

### Post by several on 2007-10-19
ok, i will try this.. just need to find out what "repositories" is :-) Translation tool matches r useless :-/

---

