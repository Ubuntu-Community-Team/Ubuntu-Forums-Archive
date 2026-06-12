---
title: "Aptitude list manually installed packages"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by zhangweiwu on 2009-12-26
Does anyone knows how can I list manually installed packages with aptitude? Or something like the 'world' file in Gentoo.

What I mean is, when you install package A have deps package B and C, more later you install package D, E, F, that has deps G, H, etc.
And what I want is a way to see in a list, command line or whatever, what packages I INSTALLED,the packages A, D, E, and F. This packages where installed manually, by me.

So far the closest thing I can get is
```

aptitude search '~i!~E' | grep -v "i A" | cut -d " " -f 4

```

As seen on 
[http://www.debian-administration.org/articles/462](http://www.debian-administration.org/articles/462)

However this method only gives me packages marked as manually installed, which is not the packages installed manually. The difference is, it listed all packages installed by Ubuntu installer, which are marked as manually installed but not manually installed.

I need the list of packages 'really' manually installed because the list of packages that are marked as manually installed doesn't help much when I switch from 32-bit to 64-bit or back, as package names are not exact match between them. It also is not helpful if I got a Ubuntu 9.10 new computer where i want to have my applications, when I only had an old computer with Ubuntu 8.04 (this indeed happened, I cannot upgrade that neither because ubuntu stopped ppc support by that time).

Thanks in advance!

---

### Post by SecretCode on 2009-12-26
> **zhangweiwu said:**
> However this method only gives me packages marked as manually installed, which is not the packages installed manually. The difference is, it listed all packages installed by Ubuntu installer, which are marked as manually installed but not manually installed.

I had to read this three times ... are you saying that you want a list of all the packages you have manually installed *after* installing Ubuntu, excluding packages automatically installed (which you've managed to exclude) and all packages installed as part of Ubuntu initial setup?

I don't know of a way of doing that. I don't think apt/aptitude keep any record of this distinction.

What I have done is to save a list of packages existing straight after installation and then compare the new list (actually I installed a fresh Ubuntu in a virtual machine to get the base list).

---

### Post by zhangweiwu on 2009-12-26
> I had to read this three times ... are you saying that you want a list of all the packages you have manually installed after installing Ubuntu, excluding packages automatically installed (which you've managed to exclude) and all packages installed as part of Ubuntu initial setup?

True! Thank you to be this patient to read it 3 times to get what I asked:)

> 
What I have done is to save a list of packages existing straight after installation and then compare the new list (actually I installed a fresh Ubuntu in a virtual machine to get the base list).


Right. It is better than having no solution... Thanks.

---

### Post by zhangweiwu on 2009-12-28
I am thinking, if the packages installed by Ubuntu installer have some characteristics, it should be picked out easily. For example, what is the file last written during installation? I expect the installation log, so any package installed before the modification time of installation log should be installed by the installer. How practically this can be done I don't know. I am new to Ubuntu world.

---

### Post by SecretCode on 2009-12-28
I'm not optimistic about that approach ... any package installed at system installation time could be updated later. That would affect the timestamps of files. Plus, each package could contain many files - to identify them you'd need to get the list of files for each.

---

### Post by wedesoft on 2011-01-18
You can list the manually installed packages as follows:

    ```
aptitude search '!~M ~i' -F '%p'
```

**!~M** selects *not automatically selected* packages and **~i** selects *installed* packages. See content of package **aptitude-doc-en** for more information.

---

