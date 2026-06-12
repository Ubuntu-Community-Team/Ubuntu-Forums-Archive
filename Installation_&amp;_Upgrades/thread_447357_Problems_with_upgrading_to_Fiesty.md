---
title: "Problems with upgrading to Fiesty"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by lblitzer on 2007-05-17
Hi there, I'm a new user to Ubuntu and I've given Edgy a couple days to sit on my current PC.

After a couple days of swapping my components so that I could load Ubuntu with ease, I've decided I want to upgrade to Fiesty Fawn.

I downloaded the upgrade just fine, but when I try and install it, it gives me an error and says the update has to be aborted.

Now I can't get even get into the Update Manager, because it's giving me this (from the terminal):

```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  file-roller: Depends: unzip but it is not installed

  libgtkhtml3.8-15: Depends: lib but it is not installable or
                             render1 but it is not installable
  ubuntu-artwork: Depends: feisty-wallpapers (>= 0.9-0ubuntu3) but it is not installed
  ubuntu-desktop: Depends: unzip but it is not installed
  ubuntu-standard: Depends: dselect but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

It's driving me mad, and I'd like a more simple solution to this. Any help is appreciated!

Edit: The Update Manager is giving me the error "Software Index is broken!" further saying, "It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

And I've tried the terminal commands listed and it doesn't do much of anything.

---

### Post by lblitzer on 2007-05-18
Apparently I downloaded Edgy only a week before Fiesty came out! Argh. Luckily, I recently just installed this, so I'll just burn Fiesty and run that!

---

