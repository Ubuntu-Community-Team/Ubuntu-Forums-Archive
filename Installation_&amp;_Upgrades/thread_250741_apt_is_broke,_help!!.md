---
title: "apt is broke, help!!"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by nicstevens42 on 2006-09-04
Hi 

I tried to install a .deb package for jEdit and now my apt doesn't work. When I had fedora and suse I could rebuild the RPM lists. I don't know how to do this with apt. 

these are the errors I'm getting

```
E: The package jedit needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

Any ideas are greatly appreciated!

---

### Post by FakeOutdoorsman on 2006-09-04
This sounds like a similar problem to:

[problems with synaptic package manager]("http://www.ubuntuforums.org/showthread.php?t=232849") (mentions jedit)

or

[apt-get ERROR - Please help me!!]("http://www.ubuntuforums.org/showthread.php?t=39563")

---

### Post by Uluen on 2006-09-04
You could try
```
$ sudo apt-get clean
```
```
$ sudo apt-get update
```
```
$ sudo apt-get -f install
```
See if that helps.

---

### Post by nicstevens42 on 2006-09-04
> **Uluen said:**
> You could try
```
$ sudo apt-get clean
```
```
$ sudo apt-get update
```
```
$ sudo apt-get -f install
```
See if that helps.

Tried all of those ... they didn't help.

---

### Post by nicstevens42 on 2006-09-04
> **FakeOutdoorsman said:**
> This sounds like a similar problem to:

[problems with synaptic package manager]("http://www.ubuntuforums.org/showthread.php?t=232849") (mentions jedit)

or

[apt-get ERROR - Please help me!!]("http://www.ubuntuforums.org/showthread.php?t=39563")


I'll try those. Thanks! :D

---

