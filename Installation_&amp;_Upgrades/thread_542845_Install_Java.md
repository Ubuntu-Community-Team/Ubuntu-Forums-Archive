---
title: "Install Java"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by timboellis on 2007-09-04
Can someone help with installign java so that I can play those 360's and the like through firefox as I have read through all the posts and none can help me any suggestions.

---

### Post by wolfen69 on 2007-09-04
java is in synaptic package manager. first go to system>administration>software sources and make sure all repositories are checked off.

---

### Post by timboellis on 2007-09-04
I am using Kubuntu and cannto find the settings you suggested

---

### Post by wolfen69 on 2007-09-04
you did not say you were using kubuntu. anyway, open adept package manager and search for java.

---

### Post by ptillemans on 2007-09-04
Or from the command line (GUI agnostic) :)

aptitude install sun-java6-jre

note these packages are coming from the multiverse repo so you might need to remove the comments in /etc/apt/sources.list from the lines with multiverse.

Peter

---

