---
title: "Ubuntu Software Center : strange error message"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by alain.roger on 2011-11-12
Hi,

since today i get the following error message from Ubuntu Software Center when i try to install a new software.
```
   	 	 	 	 	 	  The following packages have unmet dependencies: 
  
 libqtcore4:i386: libqtgui4:i386: Depends: libqt4-declarative (= 4:4.7.4-0ubuntu8) but 4:4.7.4-0ubuntu8 is installed 
                 Depends: libqtcore4 (= 4:4.7.4-0ubuntu8) but 4:4.7.4-0ubuntu8 is installed 
 
```

i checked the Edit > Software Sources > Other Software and i have:
```

http://extras.ubuntu.com/ubuntu (source codes + standard)
http://ppa.launchpad.net/webupd8team/themes/ubuntu (standard + source code)
http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu (standard + source code)

```
all those are checked and all others are unchecked.

so what could be the problem ?
thx.

A.

---

### Post by alain.roger on 2011-11-12
Ok, so i solved my problem using terminal as following:
1. sudo apt-get -f install
2. remove all files having the same name but not the same version
3. once again i run sudo apt-get -f install to review if everything is ok
4. sudo apt-get update
5. and later on review if Ubuntu Software Center is ok

---

