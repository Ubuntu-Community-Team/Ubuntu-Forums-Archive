---
title: "terminal apt-get error"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by jeremygjohn on 2008-05-11
ok i try to do sudo apt-get install wine 
i get this error:
package wine not available, but is referred to by another package 
This may mean that the package is missing, has been obsoleted or is only available from another source
E: package wine has no installation canidate

i did not used to get this error?

---

### Post by jeremygjohn on 2008-05-11
bump:mad:

---

### Post by RATM_Owns on 2008-05-11
Use these two commands:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

Then try again.

---

### Post by jeremygjohn on 2008-05-11
does not work.. i get different errors now lol.

---

### Post by bapoumba on 2008-05-11
wine is in universe, you need to enable these repos. Please post your sources.list:
```
cat /etc/apt/sources.list
```

---

