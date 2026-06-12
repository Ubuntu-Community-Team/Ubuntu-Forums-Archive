---
title: "Synaptic Errors"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by mfmbcpman on 2006-11-27
I am getting the following error message when I attempt to open Synaptic Package Manager. It shows 0 packages installed and 0 available. It says it might be because of a bad network connection when I try to reload the package information but I'm online right now typing this. 

```
E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
E: Unable to lock the list directory
```

---

### Post by mfmbcpman on 2006-11-30
Come on, this cannot be that hard.

---

### Post by jabberwoki on 2006-11-30
> **mfmbcpman said:**
> I am getting the following error message when I attempt to open Synaptic Package Manager. It shows 0 packages installed and 0 available. It says it might be because of a bad network connection when I try to reload the package information but I'm online right now typing this. 

```
E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
E: Unable to lock the list directory
```

Is your non-free repository enabled in your sources.list? 
you can do this through synaptic, select "repositories" from the menu at the top

you could also try uninstalling flashplugin-nonfree, that might satisfy synaptic or  run "sudo apt-get -f install" from the command line
 to "fix" the problem 
I'm not an expert but these things have worked for me in the past
hope it helps

---

