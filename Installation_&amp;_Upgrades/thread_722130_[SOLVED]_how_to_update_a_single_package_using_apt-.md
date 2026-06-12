---
title: "[SOLVED] how to update a single package using apt-get?"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by undecidable on 2008-03-12
how to update a single package using apt-get?

1.  I know I can list all updateable pkgs with :
  apt-show-versions -u  
or  apt-get -u upgrade

2. I know I can update all the updateable pkgs with
  apt-get upgrade

But if I just want to update one package, how do I do it?

Can I just do
apt-get install <pkg>
and apt-get will know that the pkg is already installed and do an update?

Or should I remove the pkg first then install:
apt-get remove <pkg>
apt-get install <pkg>

Any guidance appreciated.

---

### Post by jan quark on 2008-03-12
try 

```
sudo apt-get install whatever
```

if there is a newer version in the repositories apt-get is going to see this and hopefully upgrade it :)

---

### Post by _xray7224 on 2008-03-12
To use apt-get you type to get a package 
```
sudo apt-get install package-name
```

to remove the package using apt-get you need to type

```
sudo apt-get uninstall package-name
```

for example if you were wishing to install something like kde on your ubuntu you would type this

```
sudo apt-get install kubuntu-desktop
```

and if you wanted to remove Gnome you would type

```
sudo apt-get uninstall ubuntu-desktop
```

hope this helps and good luck !!!

---

### Post by undecidable on 2008-03-12
_xray7224

while in general I am very grateful to receive help,
you really do need  to read the question first.

regards

---

### Post by PmDematagoda on 2008-03-12
Try:-
```
sudo apt-get upgrade nameofpackage
```

---

### Post by prshah on 2008-03-12
> **undecidable said:**
> how to update a single package using apt-get?

Can I just do
apt-get install <pkg>
and apt-get will know that the pkg is already installed and do an update?

Any guidance appreciated.

Yes that is correct. "sudo apt-get install <alreadyinstalledpackagename>" will inform you if you already have the latest availible version. If a newer version is available. it will ask for confirmation before updating that particular package and it's dependencies.

Cheers,
PRShah

---

### Post by undecidable on 2008-03-12
PmDematagoda

Are you sure about this??

a.  the man page for apt-get doesn't show that the 'upgrade' action can have a parameter
(but does show that install and remove can have <packagename> as a parameter.)

b.  The man page specifically says:
"upgrade is used to install the newest versions of all packages"
and not that it can be used to upgrade a specific package.  

thanks
mc

---

### Post by undecidable on 2008-03-12
> **prshah said:**
> Yes that is correct. "sudo apt-get install <alreadyinstalledpackagename>" will inform you if you already have the latest availible version. If a newer version is available. it will ask for confirmation before updating that particular package and it's dependencies.

Cheers,
PRShah

PRShah

Thanks for bringing clarity to this question.
Yours will remain the definitive answer.
(and if I can remember how to do it, I will mark this thread solved)

---

