---
title: "Installing GDL"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by Sergei Schmalz on 2011-02-14
Greetings!

I run Ubuntu 10.10 within the VirtualBox. Although I'm new to Ubuntu I badly need to install GDL (to be able to use NASA's SolarSoft for image reduction), so I tried it following the descriptions given by Kenneth Desmond ([click me]("http://www.physics.emory.edu/students/kdesmond/InstallingGDL.html")) with the only difference, that he is writing there about **gdl-0.9rc1**, while I downloaded the latest **gdl-0.9.tar.gz**.

After deleting the **FALSE** parameter within the file **plot3d_nr.cpp** I proceeded with installation and the first problem that I encountered while doing **sudo apt-get install netcdfg-dev libhdf5-serial-dev libplplot-dev plplot9-driver-xwin libhdf4g-dev libreadline5-dev gsl-bin libgsl0-dev** was the message:
> Unable to locate package netcdfg-dev
What to do?

The rest was installed properly.

Then, when I ran **./configure --with-python=no** it did well in the beginning, scrolling line by line further, but when it came to the line:
> checking for stifle_history in -lreadline... no
it showed me an error message:
> Error! GNU readline was not found.
Use --with-readlinedir=no to explicitely disable it
Check the README or use configure --help for other libraries needed
What to do?

And finally, I just ignored the above two errors and went on with installation process and did **make**, and it just told me:
> make: *** No targets specified and no makefile found. Stop.
What should I do about this?

Similarly, after I ignored this and did **sudo make install** it also told me:
> make: *** No rule to make target 'install'. Stop.
What does this mean?

I'd appreciate any help. Many thanks in advance!

---

### Post by Sergei Schmalz on 2011-02-15
Anybody any help?

---

### Post by FrenchyFungus on 2011-02-18
> **Sergei Schmalz said:**
> Greetings!

I run Ubuntu 10.10 within the VirtualBox. Although I'm new to Ubuntu I badly need to install GDL (to be able to use NASA's SolarSoft for image reduction), so I tried it following the descriptions given by Kenneth Desmond ([click me]("http://www.physics.emory.edu/students/kdesmond/InstallingGDL.html")) with the only difference, that he is writing there about **gdl-0.9rc1**, while I downloaded the latest **gdl-0.9.tar.gz**.

After deleting the **FALSE** parameter within the file **plot3d_nr.cpp** I proceeded with installation and the first problem that I encountered while doing **sudo apt-get install netcdfg-dev libhdf5-serial-dev libplplot-dev plplot9-driver-xwin libhdf4g-dev libreadline5-dev gsl-bin libgsl0-dev** was the message:

What to do?

The rest was installed properly.

Then, when I ran **./configure --with-python=no** it did well in the beginning, scrolling line by line further, but when it came to the line:

it showed me an error message:

What to do?

And finally, I just ignored the above two errors and went on with installation process and did **make**, and it just told me:

What should I do about this?

Similarly, after I ignored this and did **sudo make install** it also told me:

What does this mean?

I'd appreciate any help. Many thanks in advance!
It's in the repositories.

```
sudo apt-get install gnudatalanguage
```

A newer version is also available here: [http://aramis.obspm.fr/~coulais/IDL_et_GDL/Ubuntu/Packaging-Download_pageFR.html](http://aramis.obspm.fr/~coulais/IDL_et_GDL/Ubuntu/Packaging-Download_pageFR.html)

That page is in French, though. Look for "Paquets binaires disponibles gdl-0.9rc4" then choose the right architecture beside "Pour Ubuntu 10.04 LTS"

Or use Google Translate...


EDIT: run with "gdl"

---

