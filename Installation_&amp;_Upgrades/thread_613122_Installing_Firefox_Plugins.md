---
title: "Installing Firefox Plugins"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by Trapezium on 2007-11-14
Apologies if this has already been addressed (and I have no doubts that it has), but I had a quick look and couldn't find anything on the subject:

I'm sure it's pretty simple, but how do I install the plugin(s) necessary to use Java-based programs in Firefox?

---

### Post by taurus on 2007-11-14
You want java plugins!

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
java -version
```

---

### Post by Trapezium on 2007-11-14
Thanks for your help, but this popped up: "E: Couldn't find package sun-java6-bin."

Any ideas?

EDIT: If I've already got the plugin on the system from a Windows install, would it be possible to just move the file to another folder? If so, where?

---

### Post by taurus on 2007-11-14
Which release are you running?  Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by mattroingojs on 2007-11-14
I recommend you install Ubuntu 7.10, It automatic upgrade plugin for firefox.

---

### Post by trevorsowers on 2007-11-14
I am having the same problem and I have tried all the suggestions I could find in this forum.  None worked!!!!   I can use java just fine with kazehakase browser but not firefox.

---

