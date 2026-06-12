---
title: "Ubuntu Software Center - Problem"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by thenailedone on 2010-04-08
Hello,

When I try and install any application with the Ubuntu Software Center I get the following error:

> **Requires installation of untrusted packages**

The action would require the installation of packages from not authenticated sources.


I know I can install the applications with apt-get but if I don't have to why should I?

---

### Post by ubunterooster on 2010-04-08
Sounds like you edited sources list?

---

### Post by thenailedone on 2010-04-08
> **ubunterooster said:**
> Sounds like you edited sources list?

Nope... did install from the Beta source CD and updated...

---

### Post by QLee on 2010-04-08
> **thenailedone said:**
> Hello,

When I try and install any application with the Ubuntu Software Center I get the following error:

I generally see a message like that when I don't have the "signing" keyring installed for the repository from which I'm trying to download a package, thus the package can't be authenticated.

---

### Post by null_pointer_us on 2010-04-08
I got the same error when trying to install a package.

Here's what fixed it for me:

```
sudo aptitude update
```

This should re-download any gpg keys you are missing.

---

### Post by thenailedone on 2010-04-09
> **null_pointer_us said:**
> I got the same error when trying to install a package.

Here's what fixed it for me:

```
sudo aptitude update
```

This should re-download any gpg keys you are missing.

:guitar: It worked!  What I don't get is if I updated apt-get it didn't work but updating aptitude worked, can anyone explain why?

*edit: Oh well, I guess it doesn't matter, it worked... case closed :p*

---

