---
title: "MDM (Middleman Project) conflicts with MDM (Mint Desktop Manager)"
date: 2013-10-16
forum: Installation &amp; Upgrades
---

### Post by Anaximander Thales on 2013-10-16
Soo -- I'm trying to figure out if those who have installed Mint Desktop Manager (there are at least two PPA's that offer Mint Desktop Manager, the one I have is NoobsLab PPA) whether they had to install from source, or if they were able to use apt, aptitude or synaptic to install it.

I ask because there is a package in Raring and Saucy called Middleman Project/System.  If I do a search, in synaptic, for mdm, I get:
```
Utilities for single-host parallel shell scripting
  
The Middleman System (mdm) is a set of utilities that help you
parallelize your shell scripts.  Simply label the commands to run in
parallel, and the System automatically exploits every parallelization
opportunity that arises at runtime.  You can also specify dependency
between commands so that they run in an appropriate order.

Comes with an ncurses-based monitoring console.  Compatible with xargs,
find, make, any shell, together, in a script or interactively.
```

I did attempt to install this.  I did not get a login screen except on my tty screens.  An attempt to sudo service mdm start generates an unknown service error.

To install Mint Desktop Manager the instructions are this:
```
To install MDM and MDM themes in Ubuntu open Terminal (Press Ctrl+Alt+T) and copy the following commands in the Terminal:
Terminal Commands:
sudo add-apt-repository ppa:noobslab/mint
sudo apt-get update
sudo apt-get install mdm mdm-themes
```

I have tried pinning.  I am by no means competent in pinning, but followed several guides that got me to this point:
In /etc/apt/preferences
```

Package: mdm
Pin: release o=Ubuntu
Pin-Priority: -1

Package: mdm
Pin: release o=LP-PPA-noobslab-mint
Pin-Priority: 700

```

With the pinning set, mdm shows up in a search with no description and no information (i.e. no description, no dependencies, no common), but does show the version as coming from raring (as opposed to noobslab).  Marking it to install gives me a no available version error.

Here are my thoughts on how to make it work through synaptic and drawbacks or issues:
- Pinning:  Have not been able to make this work, but I'm by no means competent in this.  I've read through several guides on it, and the best I've gotten is that mdm is in the database, but no available version.

- remove the universe component from my sources.list.  However, the universe components have thunar, plymouth themes, mousepad, vpn components for network manager, etc.  This seems to be a very drastic measure that's going to cause many more problems.

- Install from source.  This will be the only package that is installed from source.  DKMS will allow me to keep Mint DM set up correctly for kernel updates, it does not automatically update Mint DM, this is still a manual process, requiring dkms changes for new Mint DM update.


Any ideas as to when the Middleman Project showed up?  Instructions for installing Mint DM showed up around July -- the most recent post I can find of people installing to ubuntu was 18 days ago ([MDM display manager and MDM themes for Ubuntu 13.04/12.10/12.04]("http://www.noobslab.com/2013/06/mdm-display-manager-and-mdm-themes-for.html")), did the Middleman System show up in the last 17 days?

I know I can't remove it from the universe components, so how do I make Mint Desktop Manager show up in apt/aptitude/synaptic?

---

### Post by Anaximander Thales on 2013-10-16
I have attempted to temporarily disabled the universe group for my distro.  That did not help.  Now that I am back home with my desktop computer, which does currently have a ppa that contains the mint desktop manager.  In looking at the packages available on that, the Mint DM is available for downloading.  So, it seems as if I have some configuration setting not set correctly (I've compared synaptic settings on both my desktop and laptop and they are equal, so it's probably in a configuration file), or I'm missing a package that'll allow the most recent version.

Work on this continues.

---

### Post by Anaximander Thales on 2013-10-16
As best as I can tell -- apt/aptitude/synaptic should be showing mdm as the mint destop manager.  It is not.

---

### Post by Anaximander Thales on 2013-10-17
Solving this by starting back from scratch.  This was a custom mini-ubuntu installation, and I think something got hosed.

---

