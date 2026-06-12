---
title: "Accidentaly removed gnome and nautalis"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by themusicwave on 2006-09-26
Well I just got myself into a bit of a problem.

On my desktop I was trying to remove a corrupt package using synaptic.  When I removed it, the delete also removed everything it depended on, which included gnome and nautalis.  

I cut the power when I realized what was happening, but it was too late.  My desktop can nome only boot into comman line only mode.

I am not to strog with the command line, but have been learning it for courses I am taking and for my own use.  

Now I need to reinstall the missing files from the command line, but I have no idea how.  I tried sudo apt-get gnome, but I received an error saying dpg was interrupted and to run dpkg --confgiure -a to correct the problem.

So at this point what do I do?  SHould I wipe the partition and start over or is there hope for me yet?

---

### Post by themusicwave on 2006-09-26
I tried entering 
dpkg --configure -a
sudo apt-get gnome-bin

and it just istalled a bunch of stuff, not sure if I fixed it though.

I also think i lost some of my gnome apps before.

---

### Post by bswilson on 2006-09-26
Just to be sure that you got all the dependencies back and everything, why not just reinstall all the desktop packages at once?

```
$ sudo apt-get update; sudo apt-get install ubuntu-desktop
```

---

### Post by themusicwave on 2006-09-26
any idea how to restore nautilus?

---

### Post by themusicwave on 2006-09-26
the ubuntu desktop part came back as an invalid operation

---

### Post by wenzlicker on 2006-09-26
The package you need to install is ubuntu-desktop (note the hyphen). That package depends on all the packages that are defaultly installed. When you accidently deleted gnome, you had to remove that package. By installing it, it will also install gnome and nautilus again.

sudo apt-get install ubuntu-desktop

---

