---
title: "Run Level"
date: 2005-01-30
forum: Installation &amp; Upgrades
---

### Post by trivialpackets on 2005-01-30
Hoping for a quick answer here.  How do you configure Ubuntu to open up without the graphical greeter and just to a terminal prompt?  Is it a setting that can be corrected via the GUI?  A file that needs to be edited to a different run level or a command that needs to be removed from the boot prompt?  Thanks in advance whomever.  On a side note, the only thing that my notebook does not do for me yet is play DVD's.  Any ideas on how to get this functioning?  Thanks in advance.

---

### Post by rudi on 2005-01-30
for a quick and dirty way to boot to a non-graphical system:
    ```

   cd /etc/init.d
   mv gdm gdm.disabled
   update-rc.d gdm remove
   
``` 
   to return to a graphical login:
    ```

   cd /etc/init.d
    mv gdm.disabled gdm
   update-rc.d gdm start 99 2 3 4 5 .
   
```

---

### Post by trivialpackets on 2005-01-31
thanks, worked out alright.  still can't install latest nvidia drivers which annoys me, but this way I can get it to function outside of X which is a step in the right direction.

---

