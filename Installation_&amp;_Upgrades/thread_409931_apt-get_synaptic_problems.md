---
title: "apt-get synaptic problems"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by edwatto on 2007-04-15
Hello,

I need some help with my package managers. When I try and install anything now using apt-get i get this output.

```

You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
fontconfig: Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-1.1ubuntu12 is to be installed
libcairo2: Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-1.1ubuntu12 is to be installed
Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5.1ubuntu0.1 is to be installed
  libcairo2-dev: Depends: libcairo2 (= 1.2.4-1ubuntu2) but 1.4.2-1 is to be installed
  libfontconfig1-dev: Depends: libfontconfig1 (= 2.3.2-7ubuntu2) but 2.3.2-1.1ubuntu12 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

At first I tryed what it said 

```
apt-get -f install
```

this didn't work. it just came up with the same output. I then went in to synaptic and it cam up with "You have 4 broken packages on your system! Use the "Broken" filter to locate them."

tried that...same problem.

What I think has happened is that I have installed "libcairo" and "libfontconfig" using non-ubuntu .deb files (ones for debian?) Is there any way I can "rollback" these or something.

thanks in advance.

---

### Post by rapolas on 2007-04-15
download those broken packages manually from packages.ubuntu.com and install them with #dpkg -i package_name.deb
for me it worked;)

---

### Post by edwatto on 2007-04-15
Thanks for the speedy reply. I'm pretty sure this will work but there's one snag.

when I download the files and try to install them I get this similar output for all of them:

```
root@ubuclient:/home/ed/Desktop# dpkg -i libcairo2_1.2.4-1ubuntu2_i386.deb
(Reading database ... 122620 files and directories currently installed.)
Preparing to replace libcairo2 1.4.2-1 (using libcairo2_1.2.4-1ubuntu2_i386.deb) ...
Unpacking replacement libcairo2 ...
dpkg: dependency problems prevent configuration of libcairo2:
 libcairo2 depends on libfontconfig1 (>= 2.3.0); however:
  Package libfontconfig1 is not configured yet.
dpkg: error processing libcairo2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libcairo2

```

how exactly do I configure libfontconfig?

thanks again

---

### Post by Treebeard on 2007-04-15
> **edwatto said:**
> 
how exactly do I configure libfontconfig?


This can do the trick :
```

sudo dpkg --configure -a

```

---

### Post by edwatto on 2007-04-15
Thanks a lot guys,

Just for the record, I did
```
sudo dpkg --configure -a
```

and then did 
```
sudo apt-get install -f
```

...and it worked. All package managing stuff now back to normal.

Thanks again.

---

