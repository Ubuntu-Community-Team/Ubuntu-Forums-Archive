---
title: "Remove Dapper installation from second hd"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by code-breaker on 2007-01-17
A few weeks ago I upgraded to edgy. I bought a new hd and did a clean install, keeping my old dapper install on the other hd intact (which now shows up as a drive on my edgy desktop). I am happy with edgy, and I now want to reclaim the space on the dapper partition by uninstalling. What is the best way to do it? Thanks.

---

### Post by DarkN00b on 2007-01-17
Open gparted, unmount the Dapper drive and format it with whatever fs you want to use on it.

---

### Post by code-breaker on 2007-01-17
Sorry, I wasn't as clear as I should have been. I have a lot of data that I want to keep on the partition, and I want to free up the space that is currently being taken up by the dapper install. 

My question is, can I simply delete all of the (filesystem) folders that I don't want? Is that the best way?

---

### Post by DarkN00b on 2007-01-18
I'm not sure about that. 

FWIW, you could copy what you want to keep to a temporary folder on your new HD, format, and then move the files to permanent storage on the old drive.

---

### Post by louieb on 2007-01-18
Don't see a problem with opening up the file manager and deleting away. 
The only problem it could cause is if you are still using the GRUB files from Dapper install. But since you installed edgy last that should not be the case.

---

