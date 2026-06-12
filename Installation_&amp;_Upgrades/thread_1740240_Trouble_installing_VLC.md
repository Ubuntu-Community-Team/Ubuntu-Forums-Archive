---
title: "Trouble installing VLC"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by Chemical_Ire on 2011-04-26
Hi there, 

I'm having trouble installing VLC through the synaptic and the terminal.

I'm getting this error:

warning, in file '/var/lib/dpkg/available' near line 27195 package 'libmono-sharpzip2.84-cil':
'Replaces' field, reference to 'mono-classlib-2.0': error in version: invalid character in version number
dpkg: parse error, in file '/var/lib/dpkg/available' near line 27195 package 'libmono-sharpzip2.84-cil':
`Replaces' field, invalid package name `
E: Sub-process /usr/bin/dpkg returned an error code (2)

I'm new to ubuntu and I'm not sure how to solve this issue. Can someone help me?

---

### Post by Dutch70 on 2011-04-26
Run this command and then try to install vlc from software center.
```
sudo apt-get update && sudo apt-get upgrade
```

If that doesn't work run these commands and try again.
```
sudo dpkg --configure -a
```
```
sudo apt-get install -f
```

What version of Ubuntu are you using?

---

