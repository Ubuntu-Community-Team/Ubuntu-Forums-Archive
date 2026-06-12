---
title: "Package synaptic is not available !?!?"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by Bao2 on 2012-04-28
Well, I am testing 12.04 and trying to install synaptic:

sudo apt-get install synaptic

it says:
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate


So is there a way to get synaptic or is this a feature to get mad all the people here? Is this a MKUltra installation experiment or something?

---

### Post by arpanaut on 2012-04-28
Did you try```
 sudo apt-get update
```before you tried the install command?

It installed fine here. (freshly installed 12.04)

---

### Post by Bao2 on 2012-04-28
Instead using the terminal to install synaptic I open Ubuntu Software Center and search for synaptic and it says:

Synaptic Package Manager
Available from the "universe" source.

And there is a button to the right "Use this Source".


I checked again the software sources and the Universe already was checked. But well, I click the button "Use this Source" and it does something (downloads two things I don't remember) and now here is the synaptic package ready to be downloaded in Ubuntu Software Center.

I click Install and it downloads. SOLVED.

But why synaptic doesn't come in the ubuntu iso. You can't live without it.

---

### Post by Bao2 on 2012-04-28
> **arpanaut said:**
> Did you try```
 sudo apt-get update
```before you tried the install command?

It installed fine here. (freshly installed 12.04)


Yes, Probably that was the reason the order on the terminal didn't work.
But well, installing it on the ubuntu software center worked.

---

### Post by MGebhart on 2012-04-28
Terminal:

sudo apt-get install synaptic

This worked for me in 12.04

SORRY, MISREAD YOUR THREAD.

---

