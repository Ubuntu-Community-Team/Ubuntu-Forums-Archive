---
title: "kernel compilation with localmodconfig and git help"
date: 2011-09-02
forum: Installation &amp; Upgrades
---

### Post by jewfromdahood on 2011-09-02
I have been trying to compile a kernel with the localmodconfig and core 2/newer xeon optimizations and was wondering what options can I use to optimize my linux box, as well as how do i make a linux kernel using the localmodconfig. I have been using this guide at [http://blog.avirtualhome.com/2011/08/03/how-to-compile-a-new-ubuntu-11-04-natty-kernel/](http://blog.avirtualhome.com/2011/08/03/how-to-compile-a-new-ubuntu-11-04-natty-kernel/) I have liked this walk through since I started using Ubuntu. And can't figure out how to use localmodconfig to use those settings as a baseline, and then further optimize from there. Thank you in advance for any responses

---

### Post by jewfromdahood on 2011-09-02
bump

---

### Post by jewfromdahood on 2011-09-06
bump

---

### Post by jewfromdahood on 2011-09-07
bump

---

### Post by pdoes on 2011-11-16
A little late, maybe to late, but for the record.

Using the walk-through as reference you have to do the following:

In the section Creating a new config replace these steps:
```
cp debian.master/config/amd64/config.flavour.generic debian.master/config/amd64/config.flavour.i7
fakeroot debian/rules clean
debian/rules updateconfigs
```

with
```
make localmodconfig
cp .config debian.master/config/amd64/config.flavour.i7
fakeroot debian/rules clean
debian/rules updateconfigs
```

If you don't want to edit the configuration any further you can jump right to the step 
> When you're done, make a backup of the config flavor file.
```
cp debian.master/config/amd64/config.flavour.i7 ../.
```

And that should do it.

---

