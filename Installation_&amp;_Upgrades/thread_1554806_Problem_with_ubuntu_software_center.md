---
title: "Problem with ubuntu software center"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by Bracchesimo on 2010-08-17
Hello!

I am having the following problem with the ubuntu software center. 
When I try to install or remove a new application (all of them), the following errors appears:

> The installation or removal of a software package failed.
E:I wasn't able to locate a file for the kbluetooth package. This might mean you need to manually fix this package. (due to missing arch): I am new to linux and I have no idea where the problem come from or how to fix it.

Can you please give me some tips, maybe some diagnostic I should do?

Thanks in advance

---

### Post by mörgæs on 2010-08-17
If you boot the machine and then run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

do you get any error messages?

If that is working: Can you install the same package through Synaptic?

---

### Post by Bracchesimo on 2010-08-17
Thanks,

I think I solved it,

I just upgraded the broken package from the synaptics,  now everything seem to work fine.

Thanks again!

---

