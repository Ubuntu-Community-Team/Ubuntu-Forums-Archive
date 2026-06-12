---
title: "update Failed"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by AAJ on 2007-02-13
Hi, 

I got this message error when I was tried to install the updates.

[COLOR="Red"][COLOR="Red"]W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/linux-restricted-modules-common_2.6.17.7-10.1_all.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/linux-restricted-modules-common_2.6.17.7-10.1_all.deb)
  404 Not Found[/COLOR][/COLOR]

Please Advice,

---

### Post by Kateikyoushi on 2007-02-13
I would say try in console.

```
sudo aptitude update
sudo aptitude dist-upgrade
```

Might be that your machine is not up to date and tries to fetch an old package. I get  404 Not Found
as well.

I checked now the current version is 2.6.17.11 you need to update your package list.

---

### Post by AAJ on 2007-02-14
I did, but the same nothing changed. I can not update :(. It asks me this question

The following packages will be upgraded:
  linux-restricted-modules-common 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.0kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] 

when i choose Y , i get this error
 
Do you want to continue? [Y/n/?] Y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  linux-restricted-modules-common 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
Writing extended state information... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted linux-restricted-modules-common 2.6.17.7-10.1
  404 Not Found

---

### Post by AAJ on 2007-02-14
resolved


Thanks,

---

