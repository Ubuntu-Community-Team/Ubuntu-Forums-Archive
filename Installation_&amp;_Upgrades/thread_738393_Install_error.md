---
title: "Install error"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by elbone on 2008-03-28
I get an error message when I try to update or install anything

I cant even open synaptic

here is the error: [IMG]http://i84.photobucket.com/albums/k26/elij1016/error.png[/IMG]

can anyone help me fix this?

---

### Post by Rocket2DMn on 2008-03-28
Open a terminal and run
```
sudo dpkg --configure -a
```
Then you can
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by elbone on 2008-03-28
Thanks that didn't help directly but it said the software index is broken plesae run: "sudo apt-get install -f"

and that fixed it thank you

---

