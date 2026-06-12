---
title: "[SOLVED] create private directory in Intrepid"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bcasanov on 2008-10-27
Hi, 

I am using Intrepid right now, and I remember hearing something about a Private folder in the Home directory that will be encrypted.  After upgrading to Intrepid, I looked, but found no Private folder.  Is there a way to create the encrypted Private folder that I think was promised in the Intrepid release?

---

### Post by nhasian on 2008-10-27
in a terminal type

```
sudo apt-get install ecryptfs-utils
ecryptfs-setup-private 
```

---

### Post by bcasanov on 2008-10-27
Thank you!

---

