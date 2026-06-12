---
title: "gcc pkg not complete"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by ubwho on 2007-05-23
New to ubuntu. I installed 7.04 (desktop version) and all seems fine except c compiler. The standard c libs & includes do not exist.  I need them for c extensions to python. I reloaded gcc pkgs but same result. Tried to install gcc-4.2 from source, but it fails because existing "C compiler cannot create executables."

Is there a full gcc pkg available for ubuntu?

or 

How to install gcc from source?

Thanks;

---

### Post by taurus on 2007-05-23
You need to install the build-essential package.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by stchman on 2007-05-23
> **ubwho said:**
> New to ubuntu. I installed 7.04 (desktop version) and all seems fine except c compiler. The standard c libs & includes do not exist.  I need them for c extensions to python. I reloaded gcc pkgs but same result. Tried to install gcc-4.2 from source, but it fails because existing "C compiler cannot create executables."

Is there a full gcc pkg available for ubuntu?

or 

How to install gcc from source?

Thanks;

Yes, for some unknown reason the C libraries (build-essential) are not installed by default.  Kind of hard to make drivers when the C compiler won't function.

Supposedly it was a security risk to install the libraries.

---

### Post by ubwho on 2007-05-23
Thanks very much for the replies! This indeed solved my problem. I have now learned two things - in addition to your answers, I have learned that "the community" is what makes ubuntu the best choice!

---

