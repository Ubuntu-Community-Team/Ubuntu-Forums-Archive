---
title: "installing new software issue."
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by ajatoi on 2007-10-04
I just added some softwares into my ubuntu and i am recieving this error when I click on ADD/ Remove Application. please help, as i want to remove some software and add new ones thanks



Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by rsambuca on 2007-10-04
Hi,  open a terminal "Applications -> Accessories -> Terminal", then enter
```
sudo apt-get update
```then
```
sudo apt-get install -f
```

---

