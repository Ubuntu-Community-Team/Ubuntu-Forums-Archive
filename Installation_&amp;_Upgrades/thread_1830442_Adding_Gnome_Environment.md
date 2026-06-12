---
title: "Adding Gnome Environment"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by Kozar on 2011-08-21
Ok, the problem is this:

I am using a more recent version of Linux Mint and I would like to install the Gnome environment into it to give me the option of using the different interfaces of Gnome and Mint.

I have attempted using synaptic package manager and the terminal commands
```
sudo apt-get install gnome
```
And each time I am greeted with the error message of 
```
gnome:
 Depends: swfdec-mozilla but it is not going to be installed
```

Requesting assistance comrades.

---

### Post by ajgreeny on 2011-08-21
> **Kozar said:**
> Ok, the problem is this:

I am using a more recent version of Linux Mint and I would like to install the Gnome environment into it to give me the option of using the different interfaces of Gnome and Mint.

I have attempted using synaptic package manager and the terminal commands
```
sudo apt-get install gnome
```And each time I am greeted with the error message of 
```
gnome:
 Depends: swfdec-mozilla but it is not going to be installed
```Requesting assistance comrades.
What do you mean by recent version of Linux Mint?  Is it Mint 11?  What desktop does it have now; Mint has gnome by default, so you must have chosen another version.

To overcome your problem use synaptic package manager, (install it if necessary) then go to the preferences, and make sure that "Consider recommended packages as dependencies" is not selected.  It may mean that the swfdec-mozilla  package is not a stopping-block for you, though I have no certainty about this.

---

### Post by Kozar on 2011-08-21
> **ajgreeny said:**
> What do you mean by recent version of Linux Mint?  Is it Mint 11?  What desktop does it have now; Mint has gnome by default, so you must have chosen another version.

I'm using Linux Mint 9, Isadora of the LXDE variety.

> **ajgreeny said:**
> To overcome your problem use synaptic package manager, (install it if necessary) then go to the preferences, and make sure that "Consider recommended packages as dependencies" is not selected.  It may mean that the swfdec-mozilla  package is not a stopping-block for you, though I have no certainty about this.

No dice... I just went and did that and got an identical error message, and then the the whole thing stopped. :<

---

