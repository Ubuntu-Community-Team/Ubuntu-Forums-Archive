---
title: "ntlmaps !work with python 2.5.1~rc1-0ubuntu3 ???"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by timbobsteve on 2007-07-13
Hi All,

I just installed a fresh version of Feisty Desktop on a VM using VMware Player (windows). I am now trying to install NTLMAPS so i can get out to the internet from behind our IIS firewall. I have downloaded the ntlmaps package manually from the ubuntu repo's to my windows box and moved it to the ubuntu vm, but when I ```
dpkg -i ntlmaps_0.9.9-4_all.deb
``` 
I get the following complains: 
```
dpkg: dependency problems prevent configuration of ntlmaps:
  ntlmaps depends on python (<< 2.5); however:
    Version of python on system is 2.5.1~rc1-0ubuntu3.
dpkg: error processing ntlmaps (--install):
  dependency problems - leaving unconfigured
Errors were encountered while processing:
  ntlmaps
```

the version seems to be above and beyond the 2.5 requirement of ntlmaps. What can I do to make it install (NOTE: I don't have access to the internet, thus the need for ntlmaps... I can however, get packages manually from my windows PC)

Thanks.
- Timbobsteve

---

### Post by penno on 2007-08-09
Painful huh. If ya still stuck, try something like

```
dpkg --force-depends-version -i ntlmaps_0.9.9-4_all.deb
```

Worked for me. ^_^

---

### Post by Antar Bolaeisk on 2007-12-17
Just out of curiosity did you get this to work as I am also having the same problems and if it did work for you what did you enter into the fields force-depends-version as I can't get anything to happen save errors.

Unknown Force/Refuse option.

Thanks in advance.

---

