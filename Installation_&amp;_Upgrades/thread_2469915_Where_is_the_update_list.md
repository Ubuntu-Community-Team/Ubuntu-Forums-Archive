---
title: "Where is the update list"
date: 2021-12-13
forum: Installation &amp; Upgrades
---

### Post by loggm on 2021-12-13
With executing 'apt-get update --print-uris', then copy the output to a website that can extract the URL to `wget`, then the downloading files are the update list of Ubuntu, where to put the files to the folder making 'apt-get install' and 'apt-get upgrade' to use the new update list?

---

### Post by deadflowr on 2021-12-13
Looking at what is outputted from the print-uris command option those all go into the /var/lib/apt/lists directory.

---

