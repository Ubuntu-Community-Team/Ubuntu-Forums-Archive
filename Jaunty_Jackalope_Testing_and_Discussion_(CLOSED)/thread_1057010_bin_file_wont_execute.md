---
title: "bin file wont execute?"
date: 2009-02-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by chris.h on 2009-02-01
I'm trying to install adobe air 1.5 but I cant get the bin file to execute... any ideas?

```

-rwxr-xr-x  1 chrishel chrishel 13553300 2009-02-01 11:38 AdobeAIRInstaller.bin
~$ sudo ./AdobeAIRInstaller.bin 
sudo: unable to execute ./AdobeAIRInstaller.bin: No such file or directory

```

It's located in my home directory and I'm trying to execute it from my home directory.

---

### Post by taurus on 2009-02-01
Are you running x86_64?

```
uname -m
```

---

### Post by chris.h on 2009-02-01
> **taurus said:**
> Are you running x86_64?

```
uname -m
```

Yes, sorry, I should have included that.

I solved this by following adobe's instructions on the following page:
[Install Adobe AIR Linux 1.5 on 64-bit Linux distributions]("http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084")

---

