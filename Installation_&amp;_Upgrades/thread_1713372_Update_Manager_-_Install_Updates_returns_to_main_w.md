---
title: "Update Manager - Install Updates returns to main window without installing updates"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by RuralRoots on 2011-03-24
For some reason Update Manager is not installing updates as of yesterday.

I have it set to check daily and notify if updates are available. It has been working without issues for well over a year now.

Update Manager tells me updates are available and presents the list of security, recommended, and other updates. All are selected to update, but when I select Install Updates in Update Manager it returns with a Reading Package Information window overlaid on the main Update Manager window  - *building dependency tree* then *reading state information* and dumps me back to the main Update Manager window without performing any update actions.

Sources are valid, no error messages.

Searched forums for similar issue without hits. 

Is there anyone that may have an idea what is needed to resolve this?

---

### Post by Dutch70 on 2011-03-24
What is the output you get when you run...
```
sudo apt-get update && sudo apt-get upgrade
```

That may give the information needed to diagnose your problem.

---

### Post by RuralRoots on 2011-03-24
> **Dutch70 said:**
> What is the output you get when you run...
```
sudo apt-get update && sudo apt-get upgrade
```That may give the information needed to diagnose your problem.
 Well, that is what has me stumped.

sudo apt-get update retrieves & lists in Terminal exactly the same updates as the graphical Update Manager.

sudo apt-get upgrade then properly retrieves and applies all the indicated updates.

It's not that I cannot update the system, it's simply that for some reason Update Manager just cycles back to itself without retrieving and applying the updates when I select Apply Updates.  Very, very  :confused:

---

