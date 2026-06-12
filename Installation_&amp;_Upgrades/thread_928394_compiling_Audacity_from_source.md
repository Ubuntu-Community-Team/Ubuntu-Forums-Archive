---
title: "compiling Audacity from source"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by coolethan on 2008-09-23
it appears the only way i can do things is to compile them from source and i'm getting the hang of things. i'm trying to install Audacity and i have extracted the .gz file to my desktop using the tar comand thing but i get this error when i put in ./configure



**input code: **
./configure

**output code: **
checking for gcc... gcc
checking for C compiler default output file name
configure:error:C compiler cannot create executables
see 'config.log' for more details

---

### Post by kostkon on 2008-09-24
> **coolethan said:**
> it appears the only way i can do things is to compile them from source and i'm getting the hang of things.
What do you mean. Why not install it using Synaptic?

---

### Post by coolethan on 2008-09-24
> **kostkon said:**
> What do you mean. Why not install it using Synaptic?

well i don't have internet on it so i cant use synaptic to download it and its dependancies. also its kinda fun to do the source code thing.

---

### Post by kostkon on 2008-09-24
> **coolethan said:**
> well i don't have internet on it so i cant use synaptic to download it and its dependancies. also its kinda fun to do the source code thing.
OK. But, to be able to compile it you'll have to install the [*build-essential*]("http://packages.ubuntu.com/hardy/build-essential") package. Fortunately, this package is on the Ubuntu CD.

So, put the Ubuntu CD in your drive, and then install it by doing
```
sudo apt-get install build-essential 
```

---

### Post by coolethan on 2008-09-24
> **kostkon said:**
> OK. But, to be able to compile it you'll have to install the [*build-essential*]("http://packages.ubuntu.com/hardy/build-essential") package. Fortunately, this package is on the Ubuntu CD.

So, put the Ubuntu CD in your drive, and then install it by doing
```
sudo apt-get install build-essential 
```


ok i tried that and it tells me:
The package build-essential is not available but is refered to by another package this may mean that the package may be missing or obsolete
E:Package has no installation candidate

i found the file on the cd and put it on my desktop and tried installing it from the package manager which it told me

Dependencies are not satisfiable: lib6-dev|libc-dev

so does that mean i have to get lib6-dev and/or libc-dev?

---

