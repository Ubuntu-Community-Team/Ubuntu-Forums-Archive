---
title: "IPcheck Installation: Can't Find Package?"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by Holzmann on 2007-03-24
This is odd. 

I am following the directions [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service").

I have done this before but now get the following error when I run:

**sudo apt-get install ipcheck**

Error:

Reading package lists... Done
Building dependency tree
Reading state information... Done
**E: Couldn't find package ipcheck**

Does this no longer exist or is something wrong with my sources.list?

---

### Post by nyinge on 2007-03-25
"ipcheck" should be in the universe repository.  Make sure it's turned on.

---

### Post by Holzmann on 2007-03-25
> **nyinge said:**
> "ipcheck" should be in the universe repository.  Make sure it's turned on.

Okay, so I uncommented that line in sources.list. I then re-ran the command and it still can't be found. I wonder if apt-get is taking te changed sources.list into consideration.

Do I have to "reboot" apt-get?

---

### Post by Holzmann on 2007-03-25
NM. apt-get update. duh.

---

### Post by qamelian on 2007-03-25
> **Holzmann said:**
> Okay, so I uncommented that line in sources.list. I then re-ran the command and it still can't be found. I wonder if apt-get is taking te changed sources.list into consideration.

Do I have to "reboot" apt-get?

You need to update the cache by doing the following in a terminal:
```
sudp apt-get update
```

---

