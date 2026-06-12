---
title: "linux-image-4.15.0-112-generic fails to &quot;upgrade&quot;"
date: 2020-12-14
forum: Installation &amp; Upgrades
---

### Post by helen314 on 2020-12-14
Please hepl me to resolve , my OS is unable to install C++ library due to this error : 


```

f@f-SATA:~$ sudo apt upgrade
[sudo] password for f: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-image-4.15.0-112-generic : Depends: linux-modules-4.15.0-112-generic but it is not going to be installed
E: Broken packages
f@f-SATA:~$ 



```

---

### Post by ajgreeny on 2020-12-14
I assume from the kernel version in use that you are using 18.04 but please give us all the details with the output of terminal command ```
inxi -Fzx
``` which will show us more info about hardware and software in use.

---

### Post by deadflowr on 2020-12-14
```
sudo apt update
``` 
should be run before any and all apt upgrade or install commands.
The 4.15.0-112 kernel is really old.
Currently it should be 4.15.0-128.

---

