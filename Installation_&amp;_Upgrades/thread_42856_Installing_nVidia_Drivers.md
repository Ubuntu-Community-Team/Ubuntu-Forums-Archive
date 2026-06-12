---
title: "Installing nVidia Drivers?"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by Prudentissimus on 2005-06-19
When I attempted to install the latest Linux nForce2 Drivers for my Utunbu,...

it says "Cannot find Kernel Source Tree."

How do I fix that.

---

### Post by Xian on 2005-06-19
Just a guess but you probably need to issue the command below from a terminal, and then you'll need to extract that (assuming it is a tarred package) in your /usr/src directory, and finally make a 'linux' symlink to the kernel source.

```
$ sudo apt-get install linux-tree
```

Edit: If you get that kernel tree downloaded, then issue the command below and post back with the output. That way we can give you specific instructions on what to do next. My guess is that you'll end up with a file there named 'linux-source-2.6.10.tar.bz2 ' that needs to be extracted, and that it will in turn provide a kernel source and kernel patch directory.

```
$ ls /usr/src
```

---

### Post by Prudentissimus on 2005-06-20
ok lemme reboot and try it

---

### Post by Prudentissimus on 2005-06-20
[QUOTE=Prudentissimus]ok lemme reboot and try it[/QUOTE]
 it says linux-tree cannot be found...

and when I load up ls of usr/src

there's 2 things in Blue:

the kernel headers in different versions. 2.01 i think...

---

### Post by afonic on 2005-06-20
Do you really need the nForce2 drivers? I have tried Ubuntu in a Abit NF-7S machine (nForce2 Ultra) and everything works fine without them.

---

### Post by darkpark on 2005-07-01
i just installed ubuntu 5.04 and it seems to detect my nforce2 chipset (audio, nic, and ide controller) but i can't get any connectivity.  i've got an abit nf7-s2 motherboard.
my machine worked fine under windows xp.  anyway, any adice?

on a side note, is there a way to download packages via apt-get and then copy them to another ubuntu machine?

thank you in advance.

---

