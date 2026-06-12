---
title: "keepass2 font size almost invisible after upgrade to 22.10"
date: 2022-11-22
forum: Installation &amp; Upgrades
---

### Post by dwater on 2022-11-22
Hi,

Does anyone know how to increase the font size in the keepass2 app? It was small before, but now it's almost impossible to read.

I did try some suggestions I found online, but they relate to other versions of keepass (X/XC) which seem to be based on Qt. However, keepass2 seems to be a 'mono' app:

```
$ cat /usr/bin/keepass2
#!/bin/sh
exec /usr/bin/cli /usr/lib/keepass2/KeePass.exe "$@"
$ man cli
Mono(mono)                                                          Mono(mono)


NAME
       mono  -  Mono's ECMA-CLI native code generator (Just-in-Time and Ahead-
       of-Time)
...
```

Any pointers?

---

### Post by ActionParsnip on 2022-11-22
[https://keepass.info/help/base/faq_tech.html#guifont](https://keepass.info/help/base/faq_tech.html#guifont)

---

### Post by dwater on 2022-11-22
Yeah, I'd seen that, but it hasn't lead to any solution.

> [COLOR=#000000][FONT=Verdana]KeePass uses the default graphical user interface (GUI) font that has been specified in the operating system settings.

If this was the problem, wouldn't the rest of the GUI also be 'small'? I can change the size of the test using the ubuntu a11y settings (ie 'Large Text' toggle -> on), but they have no effect on Keepass2.

[/FONT][/COLOR]> 
[LIST]
[*]On Linux systems with KDE 5 or higher, the font can be changed in the system settings &#8594; 'Fonts'.
[*]On Linux systems with GNOME 3 or higher, the font can be changed using GNOME Tweaks &#8594; 'Fonts'.
[/LIST]

I'm not sure which of the above Ubuntu uses.

> [COLOR=#000000][FONT=Verdana]In addition to supporting these system settings, KeePass allows to customize the fonts that are used in lists and for passwords (in the options dialog; these settings affect KeePass only, no other applications).[/FONT][/COLOR]

I think the above doesn't apply because it is the entire UI which has small text, so I think it's something more general than specific to 'list's and 'passwords'.

WDYT?

---

