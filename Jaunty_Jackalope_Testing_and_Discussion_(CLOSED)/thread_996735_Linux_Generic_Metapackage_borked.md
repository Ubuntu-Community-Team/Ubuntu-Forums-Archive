---
title: "Linux Generic Metapackage borked?"
date: 2008-11-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-11-29
Cruft remover has a long way to go with testing. It turfed my test box and Im in the process of getting it back together.

X wont start because the NVIDIA module has problems, and I cant reinstall the nvidia module because I cant install the linux generic metapackage, which I need for the headers in the driver compile.

Anyone else got this? Hopefully it wont last long and the devs will fix it soon so I can get back to testing :)

---

### Post by Nullack on 2008-11-29
Arg! DKMS fails to build the .28 nvidia kernel module on the linux .28-ub kernel revision.....

---

### Post by plun on 2008-11-29
> **Nullack said:**
> Arg! DKMS fails to build the .28 nvidia kernel module on the linux .28-ub kernel revision.....

See the kernel thread where autocrosser got the same.

tty is also probably broken for you..

No problem to install nVidia 180.08 within recovery.


Alberto is looking at this issue but it can take time, 180.08 is also a beta driver.

---

### Post by Nullack on 2008-11-29
Its still broken, unmet dependencies exist when trying to install the linux metapackage for the .27 current kernel. It probably wont be fixed until Monday I gather now that the weekend has set in :(

---

### Post by plun on 2008-11-30
> **Nullack said:**
> Its still broken, unmet dependencies exist when trying to install the linux metapackage for the .27 current kernel. It probably wont be fixed until Monday I gather now that the weekend has set in :(

OK...

But what is broken....:confused:

```
sudo apt-get install ubuntu-desktop

sudo apt-get install linux
```


Or use aptitude for even better suggestions.....break risk.

The cruft thing is something special...I tested Grub 2 and it was also something.

---

### Post by Nullack on 2008-11-30
linux-generic:
 Depends: linux-image-generic but it is not going to be installed
 Depends: linux-restricted-modules-generic but it is not going to be installed

linux-restricted-modules:
 Depends: linux-restricted-modules-generic but it is not going to be installed

---

### Post by plun on 2008-12-01
> **Nullack said:**
> linux-generic:
 Depends: linux-image-generic but it is not going to be installed
 Depends: linux-restricted-modules-generic but it is not going to be installed

linux-restricted-modules:
 Depends: linux-restricted-modules-generic but it is not going to be installed

I cannot see this breakage myself and one way is to follow it "deeper".

linux-restricted-modules-generic   > output and so on.

Also to look at aptitude solutions.

---

### Post by DougieFresh4U on 2008-12-01
> **Nullack said:**
> linux-generic:
 Depends: linux-image-generic but it is not going to be installed
 Depends: linux-restricted-modules-generic but it is not going to be installed

linux-restricted-modules:
 Depends: linux-restricted-modules-generic but it is not going to be installed

I installed the .28 generic last nite with out it bitchin about dependency hell and re-installed 'ubuntu-desktop' as well. Rebooted and all is good including sound. *fingers crossed*

'.28 linux-restricted-modules-generic' is not seen yet

---

