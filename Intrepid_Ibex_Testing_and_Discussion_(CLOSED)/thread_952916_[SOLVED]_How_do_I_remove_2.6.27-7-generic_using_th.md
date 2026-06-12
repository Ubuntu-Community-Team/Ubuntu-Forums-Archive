---
title: "[SOLVED] How do I remove 2.6.27-7-generic using the terminal?"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bwallum on 2008-10-19
Hi

I have managed to lose the GUI by removing some files marked as 'partial' in the update manager.

I would like to roll back to an earlier kernel version but first would like to remove the -7 kernel and any associated files.

How do I do that from the command line please?

Regards
Bob

---

### Post by gjoellee on 2008-10-19
you can just boot up with an earlier kernel and uninstall the latest kernel in Synapic.

When you have those 3 seconds or press Esc option simply press Esc and chose an earlier kernel

but if you want to remove the kernel from command line it is:
```
sudo apt-get remove <packagename>
```remember to replace the <packagename> with the real packagename or part of the package name with a "*" on the end...

---

### Post by bwallum on 2008-10-20
Thanks gjoelle

I had managed to remove the entire X environment so no gui whatsoever. This is how I recovered.

When the system boots it leaves you with a command line. Use your normal log on and password then make sure your system is up to date with
Code:

```
sudo apt-get update
```Then reinstall your desktop with
Code:```
sudo apt-get install ubuntu-desktop
```
Thanks again
Bob

---

