---
title: "All default program got removed"
date: 2012-04-14
forum: Installation &amp; Upgrades
---

### Post by kamlesh_engg on 2012-04-14
Hi all,
 I run the following command on the terminal and all of my default software such as Libreoffice etc got removed.

sudo apt-get install gtk

i ran the above command and eveything is gone. Does any one know how to get back all those program??

even ubuntu sofware centre and setting are gone.. 

why should install command removed my software ?????

---

### Post by 2F4U on 2012-04-14
What version of Ubuntu and what desktop are you using? If you are using Unity, it should be sufficient to re-install the package ubuntu-desktop, since that would pull all the default programs.

---

### Post by kamlesh_engg on 2012-04-20
i am using ubuntu 11.10
how can i reinstall ubuntu desktop ??

---

### Post by jerrrys on 2012-04-20
sudo apt-get install gtk

That command will do nothing.  No such package.

Try this:

sudo apt-get install -f

That will attempt to fix broken packages.  get any errors?

---

### Post by lisati on 2012-04-20
As well as Jerrys's suggestions, try:
```

sudo apt-get install --reinstall ubuntu-desktop

```

---

