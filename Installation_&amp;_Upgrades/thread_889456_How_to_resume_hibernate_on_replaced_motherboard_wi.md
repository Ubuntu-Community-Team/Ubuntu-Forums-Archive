---
title: "How to resume hibernate on replaced motherboard with windows xp installed"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by jmlthr on 2008-08-14
:KS I replaced my motherboard. Previous was Intel now it is VIA. My previously Windows XP installation on Intel board with Intel videos drivers hibernated correctly on new board but did not resume. I installed correct video driver for VIA board. At resuming Windows it gives following message.
“The system could not be restarted from its previous location because the restoration image is corrupt. Delete restoration data and proceed to system boot menu.”
All methods failed to correct this problem. No website over internet provides any solution to this problem! Please help.

---

### Post by prshah on 2008-08-14
> **jmlthr said:**
> 
“The system could not be restarted from its previous location because the restoration image is corrupt. Delete restoration data and proceed to system boot menu.”

This should be posted in the Windows forums; 

Solution: Delete the c:\hiberfil.sys file. Click Start-Run, then give the following commands```
cmd
attrib -s -h -r -a \hiberfil.sys
del \hiberfil.sys

``` Subsequent hibernate / resumes will work correctly.

---

### Post by jmlthr on 2008-08-14
Tried this sloution in the first place. Problem persisted.

---

