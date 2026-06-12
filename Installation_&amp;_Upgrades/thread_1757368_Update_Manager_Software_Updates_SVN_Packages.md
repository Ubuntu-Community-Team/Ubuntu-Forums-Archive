---
title: "Update Manager: Software Updates SVN Packages"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2011-05-13
Hello,

I have an application 'YaCy,' that I originally installed from the repositories; but get's updates from subversion.  When attempting to upgrade this package through update-manager, I get the following message:

**Requires installation of untrusted packages**

The action would require the installation of packages
from not authenticated sources.

***Is there anyway to override this setting???***

See attachment:




Thanks Hannibal

---

### Post by zvacet on 2011-05-15
If you trust the source just install it.

---

### Post by coljohnhannibalsmith on 2011-05-15
It won't let me...

---

### Post by zvacet on 2011-05-15
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by coljohnhannibalsmith on 2011-05-15
> **zvacet said:**
> ```
sudo apt-get update && sudo apt-get upgrade
```


Thank you...  I get this; that's how I've been doing it. But it's a lot of extra effort; and I'd like to be able to authorize this action from witin the GUI...  [COLOR=Blue]***Maybe, by checking a box and entering the root password again???***[/COLOR]





[COLOR=Blue]***Thanks Hannibal***[/COLOR]

---

### Post by zvacet on 2011-05-16
You can do it from synaptic.In** synaptic>referesh>mark all updates**.

---

### Post by coljohnhannibalsmith on 2011-05-16
> **zvacet said:**
> You can do it from synaptic.In** synaptic>referesh>mark all updates**.

Thanks,

This worked reasonably well; but I'd still like to authorize this action from within the normal Update Manager window.





Hannibal

---

### Post by coljohnhannibalsmith on 2011-05-17
This problem now appears to be solved...

[IMG]http://tshirtgroove.com/wp-content/uploads/2008/10/problem-solved-tshirt.jpg[/IMG]

---

