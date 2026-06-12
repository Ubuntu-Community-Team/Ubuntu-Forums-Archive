---
title: "Error can't install?"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by Whiteice on 2008-01-19
Hi haveing a issue with the update manager. I go to applications/add and remove and search for vlc i check mark the box and get this message

Cannot install 'vlc'

This application conflicts with other installed software. To install 'vlc' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

i went into synaptic but did not find anything out of the ordinary. can anyone help.

---

### Post by Pumalite on 2008-01-19
Post the exact error message (copy and paste here)

---

### Post by Whiteice on 2008-01-19
That was the exact error message.

---

### Post by Pumalite on 2008-01-19
At the Terminal, run:
sudo apt-get install vlc
(copy and paste the output here)

---

### Post by Whiteice on 2008-01-20
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.8.6.release.c-0ubuntu5) but it is not going to be installed
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
       Depends: ttf-dejavu but it is not installable
E: Broken packages
whiteice@whiteice-l

---

### Post by Pumalite on 2008-01-20
Try:
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

---

### Post by Whiteice on 2008-01-21
same thing is still happing even after the update and upgrade.

---

### Post by zvacet on 2008-01-21
System>administration>software sources>chek all boxes under Ubuntu software and under updates tab.Reload.

```
sudo apt-get install vlc
```

---

### Post by Whiteice on 2008-01-21
OMG thank you all so much. I feel like a complete idiot for not looking there. So a basicly my problem was that the software manager tried to download the pacakages but did'nt have the source to do it from.

---

### Post by ghpk on 2008-01-22
Thanks a Ton.

I just realized that i was not able to install most applications as i was not enabling all the options in "update software sources"

thanks guys

loving Ubuntu more and more....

---

### Post by BarnyB on 2008-03-28
Fantastic, I was having the same probs. Thanks all.

---

