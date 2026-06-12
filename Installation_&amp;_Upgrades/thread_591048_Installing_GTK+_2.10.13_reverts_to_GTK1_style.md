---
title: "Installing GTK+ 2.10.13 reverts to GTK1 style"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by Chris Johnson on 2007-10-25
I'm running Ubuntu Feisty. I installed GTK+ 2.10.13 from source in order to compile the new Gimp 2.4. That all worked, but now ALL the windows in my system have reverted to GTK1-style - i.e. like this [http://www.chris-j.co.uk/miscfiles/gtk1.png](http://www.chris-j.co.uk/miscfiles/gtk1.png)

I compiled GTK+ with the standard ./configure, make, make install routine, and GIMP with
```

export LD_LIBRARY_PATH='/usr/lib/gtk-2.0/2.10.0'
ldconfig
./configure
make
sudo make install
ldconfig
```

Can anyone help in recovering my GTK2 windows? I'm concerned that something is seriously wrong, and I won't have a GUI at all if I restart...

Thanks,
-Chris

---

### Post by Chris Johnson on 2007-10-25
I've also tried reinstalling the older GTK+ 2 libs from synaptic, but it doesn't seem to have fixed anything.

---

### Post by Chris Johnson on 2007-10-25
I've now fixed this by moving back to the ubuntu repository version GTK+ 2.10.11, by doing "sudo make uninstall" in the GTK+ 2.10.113 directory, and (just for safety - may not be necessary) reinstalling the libgtk* libraries in synaptic.

Gimp 2.4 now doesn't run, of course, but at least my desktop is back to normal.

---

