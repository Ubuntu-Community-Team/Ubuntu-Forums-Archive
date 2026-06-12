---
title: "Managing Libraries Using Synaptic"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by Rea B on 2008-08-16
I am using Ubuntu 8.04.1. The Synaptic Package Manager indicates I have libpng12-dev version 1.2.15~beta5-3 installed and that it is supported by Ubuntu. 

Why doesn't Synaptic indicate the latest version (1.2.29) is available?

What is the best procedure (brief is okay) for updating to the latest version?

I am new to Linux. Any help would be appreciated.

Thanks,
Rea

---

### Post by Partyboi2 on 2008-08-16
To upgrade packages you can do it from the terminal (Applications>Accessories>Terminal)
```
sudo apt-get update
sudo apt-get upgrade
```
>  Why doesn't Synaptic indicate the latest version (1.2.29) is available? Have you got a third party repository added that has a latter version then what is in the ubuntu repo's?

---

