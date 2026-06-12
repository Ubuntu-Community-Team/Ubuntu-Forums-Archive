---
title: "uninstalling apps"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by f6e9a on 2010-08-12
OK i want to remove everything but 

1.Firefox
2.disc burner
3.video player
4.music player
5. core components



every other software (example=  games, graphics, open office  )
i need to delete  my question is  Is there any type of uninstaller that could speed up the uninstall so i wouldn't have to do every software 1 by 1

thanks for any help,

f6e9a:)

---

### Post by Sanjeevtrip on 2010-08-12
you can always use
```

dpkg -l

```
check which software you want to remove

then do
```

apt-get remove that-software-name

```

---

### Post by sahabcse on 2010-08-13
Also open synaptic manager and select the package and click removal

---

### Post by JBAlaska on 2010-08-13
```
sudo dpkg --get-selections > myPackages
```

Will get you a copy of all installed programs "myPackages" in the home dir.

---

### Post by f6e9a on 2010-08-13
> **Sanjeevtrip said:**
> you can always use
```

dpkg -l

```check which software you want to remove

then do
```

apt-get remove that-software-name

```


do u mind giving me step by step instructions plz thanks

---

### Post by f6e9a on 2010-08-13
> **sahabcse said:**
> Also open synaptic manager and select the package and click removal

how do i do that ?  sorry i am really new

---

### Post by davidmohammed on 2010-08-13
use the application "Software Centre" - click on the Installed Software option.  On the right hand side it will display all the software installed.  Just uninstall what you dont want.

---

