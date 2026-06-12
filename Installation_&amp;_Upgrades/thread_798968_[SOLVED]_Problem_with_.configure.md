---
title: "[SOLVED] Problem with ./configure"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by Despot Despondency on 2008-05-18
Hey. I'm trying to install soundKonverter from source on my gutsy distribution. (I've tried soundKonverter from the synaptic, but it only seems to be able to convert to ogg and wav files, please see [http://ubuntuforums.org/showthread.php?t=787662](http://ubuntuforums.org/showthread.php?t=787662))

I'm running ./configure in the terminal and after a while I get the following error

```

checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!

```

I've looked around and apparently I need to install libx11-dev, which I've done but I stil get the same error. Any ideas?

---

### Post by Partyboi2 on 2008-05-19
try installing xlibs-dev

---

### Post by Despot Despondency on 2008-05-19
hey, thanks for your reply. I tried that before and got the message

```

Package xlibs-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

```

I found another thread [http://ubuntuforums.org/showthread.php?t=673012]("http://ubuntuforums.org/showthread.php?t=673012")
which says that it is no longer available on gutsy and that I should try xlibs-static-dev. I've done installed xlibs-static-dev, but I still get the same message. Is there any way for me to get xlibs-dev or is there an alternative solution?

---

### Post by thotmos on 2008-05-19
I don't have xlibs-static-dev but can compile X programs (maybe because it is a metapackage). try installing in synaptic all that begins with x11proto and ends with dev like x11proto-core-dev

---

### Post by zvacet on 2008-05-19
> but it only seems to be able to convert to ogg and wav

It is not quite truth.Go to the synaptic and find soundconverter package and then right click on it.You will see what else you have to install to convert to other formats.Second option is described [here #5.]("http://ubuntuforums.org/showthread.php?t=54821&highlight=convert")

---

### Post by Despot Despondency on 2008-05-19
Hey, thanks for your replies. Thanks zvacet, I found out today that I needed to installed lame as well, which was on the list you pointed out.

I solved the earlier problem btw, I installed kdebase-dev. Not that I need it anymore. Cheers for your help anyway.

---

