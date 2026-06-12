---
title: "Cant update/install software"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by JT9161 on 2007-12-07
I'm a linux newb so here I go. Whenever I try to use add/remove programs, update manager, synaptic package manager after I put in my password and tell it to begin whatever i get the following error message: 
 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 

this has also happened in terminal so does any one know what my issue is.

---

### Post by braacken on 2007-12-07
```
sudo gedit /etc/apt/sources.list
```

Post the contents of your repo list...seems to be where updating/installing software issues arise; first troublshooting step anyway...

---

### Post by PmDematagoda on 2007-12-07
Do:-

```
sudo dpkg --configure -a
```

That could solve your problem.

---

### Post by forestpixie on 2007-12-07
> first troublshooting step anyway...

I think the first troubleshooting step - should be to read the error's you're shown :)

---

### Post by PmDematagoda on 2007-12-07
> **forestpixie said:**
> I think the first troubleshooting step - should be to read the error's you're shown :)

Big +1 forestpixie:).

---

### Post by JT9161 on 2007-12-07
> **PmDematagoda said:**
> Do:-

```
sudo dpkg --configure -a
```That could solve your problem. 

It works thanks

---

