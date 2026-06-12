---
title: "compare machines installs"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by abovenbeyond on 2008-03-12
Hello all,
I dunno if this is possible, do you?

I would like to compare installs from synaptic package manager...

Is there a file I can compare the two and know what is not on one machine that is on the other? If so what would the command be?

---

### Post by Existentialist on 2008-03-14
dpkg --get-selections

This will generate the list of installed software.

---

### Post by zvacet on 2008-03-14
To see what you have in first comp

```
dpkg --get-selections > installed-software
```

you will find text file in your home directory.Rename it to** insoft** or something and put it in second comp(you can e-mail it to yourself).In second comp run again above command and you will get ext file in your home dir.Now you have two files in home dir(because that is the place you put file from first comp) and now run 

```
diff insoft installed-software
```

To see all options with diff type** man diff**

---

### Post by abovenbeyond on 2008-03-14
Awesome... Thanks.

---

### Post by Existentialist on 2008-03-15
Sorry I probably should have been a little more thorough in my response, thanks zvacet.

---

