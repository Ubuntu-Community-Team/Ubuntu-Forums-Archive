---
title: "Install Chrome from Command Line"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by shaftesburyiv on 2010-06-30
I am installing Ubuntu Minimal and don't want to use Mozilla because in the past it has seemed too large (I wonder if that is actually true!).  How do I install Chrome from the command line?  My computer only has 4 gb of harddrive space, so I think I can really only fit one browser.  I don't think Ubuntu Minimal has synaptic.  Forums don't seem to explain how to do it with Chrome in 10.04 -

---

### Post by sisco311 on 2010-07-01
Add the ppa repo:
```
sudo add-apt-repository ppa:chromium-daily
```
Resynchronize the package index files from their sources:
```
sudo apt-get update
```
Install chromium browser:
```
sudo apt-get install chromium-browser
```

---

