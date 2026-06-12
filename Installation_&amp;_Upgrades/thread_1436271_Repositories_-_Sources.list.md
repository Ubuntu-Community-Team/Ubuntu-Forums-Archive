---
title: "Repositories - Sources.list"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by makitso on 2010-03-22
I am going to do a new 10.04 build of Ubuntu.  To keep my 9.10 applications, I plan to use the dpkg --get-selections to migrate to the new install.  However, I have also copied the sources.list from the old to the new.  The problem is that when I have done this in the past, and then do an apt-get update I get some errors about missing md5 hashes on the new system.  

My question is, when you add a new repository and need to import an MD5 key, where does that key go?  How can I move sources.list from old to new w/o those keys?

I have had this problem before with wine and its repository.  

Thanks

Rob

---

### Post by zvacet on 2010-03-22
If you want to clone your system then use 

```
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages 
sudo xargs aptitude --schedule-only install < my-packages
sudo aptitude install
```

First command will make text file named my-packages.E-mail it to yourself and after you install Lucid put it in your home directory and run other two commands.

Use default Lucid source list and if you want to add some other repos add it as in previous versions.

---

