---
title: "Problem with beryl HELP!!"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by EitherBigfoot on 2008-03-10
s

[COLOR="Red"]sry i didn't know where to post this... i know there is some fix going around that seems to work for everyone but i seem to get it to work i  have followed  these:[/COLOR]

"Open synaptic package manager, search for beryl, press ctrl+e and select version 0.1.99.2
you have to do this for beryl, beryl-core, beryl-manager, beryl-plugins, beryl-plugins-data, beryl-settings, beryl-settings-binding, libberyldecoration0 and libberylsettings0"

this

```
$ beryl-manager --no-force-window-manager
```
```
$ beryl-xgl --use-cop
```


and this
```
sudo apt-get remove 'beryl*'
```

```
sudo apt-get install beryl=0.1.99.2~0beryl1 beryl-core=0.1.99.2~0beryl1 beryl-manager=0.1.99.2~0beryl1 beryl-plugins=0.1.99.2~0beryl1 beryl-plugins-data=0.1.99.2~0beryl1 beryl-settings=0.1.99.2~0beryl1 beryl-settings-bindings=0.1.99.2~0beryl1 emerald=0.1.99.2~0beryl1 libberyldecoration0=0.1.99.2~0beryl1 libberylsettings0=0.1.99.2~0beryl1 libemeraldengine0=0.1.99.2~0beryl1
```

[COLOR="Red"]but it still isn't working 
when i do the sudo apt-get install beryl=0.1.99.2 one i get this error:[/COLOR]

[IMG]http://i26.tinypic.com/16m6p8k.png[/IMG]



[COLOR="Red"]i curently have beryl uninstalled and that is where i stoped i am also using Ubuntu Gutsy (7.10  please help![/COLOR]

---

### Post by luisromangz on 2008-03-10
Beryl is deprecated. You should use compiz fusion instead. The compiz fusion packages in Gutsy are a bit outdated (as it should, because the stable version programs' feature freeze) but there are up to date repositories out there.

---

### Post by EitherBigfoot on 2008-03-10
> **luisromangz said:**
> Beryl is deprecated. You should use compiz fusion instead. The compiz fusion packages in Gutsy are a bit outdated (as it should, because the stable version programs' feature freeze) but there are up to date repositories out there.


well could you teach me how to install compiz fusion?

---

