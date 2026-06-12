---
title: "UnRar Issue On 11.04"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by Mynds on 2011-06-23
I tried to install unrar on my 11.04. I couldn't find it "synaptic package manager". My friend uses an older version ubuntu also, when he searches on the "synaptic package manager" he finds..

I found this article..

[http://www.cyberciti.biz/faq/open-rar-file-or-extract-rar-files-under-linux-or-unix/](http://www.cyberciti.biz/faq/open-rar-file-or-extract-rar-files-under-linux-or-unix/)

But also It didn't work.. Error is..

"E: Package 'unrar' has no installation candidate"

What can I use for rar files???

---

### Post by Mynds on 2011-06-23
Same issue for dkms also..  Dynamic Kernel Module Support
-------------------------
sudo apt-get install dkms

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dkms
----------

---

### Post by mikewhatever on 2011-06-23
If you are connected to the internet, something must be wrong with the repositories. Try refreshing the package list - **sudo apt-get update**.

---

### Post by Mynds on 2011-06-23
Yes, It was about company's proxy server, I used a different proxy and it updated package manager..

---

