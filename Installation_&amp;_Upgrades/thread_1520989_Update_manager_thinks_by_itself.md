---
title: "Update manager thinks by itself"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by Sylelfa on 2010-06-30
I had Ubuntu 6.06LTS and update to 8.04. I remove some packages that i don't need  (in example, bluetooth and assistance)  and installed some others I like  (as last openoffice and thunderbird).  Well, I always do that in Debian and it worked fine.  But now, in Ubuntu, I don't why, it works untill I have to update.  Then, update manager decides by itself to install packages I don't want have and remove packages I do want.  It's *extremely* annoying.  After every update untill Lucid Lynx, I will have to do everything over and over?  Aaargggh!!!!
  I would like to know if there's some way to fix it.


Regards
Thanks in advance!

---

### Post by stlsaint on 2010-06-30
Sounds as if you are not correctly removing these packages your wanting gone. Best practice would be to purge that particular package via terminal or use the Complete removal option via synaptic package manager. 

Terminal:
```
sudo aptitude purge firefox
```

Package Manager:
Right click package->Complete removal

---

### Post by Sylelfa on 2010-06-30
I usually do Complete removal in Synaptic.  Then I erase configuration files.  But in the next upgrade is the same.  I will try it via console.  I don't know if it will work...

Thanks anyway

---

### Post by Sylelfa on 2010-07-01
Nop, via command line doesn't work.  Is the same problem.  Anyway, I will look for a solution in documentation.  May be I find something.



Thanks anyway

---

