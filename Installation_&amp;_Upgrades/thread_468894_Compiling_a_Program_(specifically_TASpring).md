---
title: "Compiling a Program (specifically TASpring)"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by cong06 on 2007-06-09
I've been following the [guide to install](http://spring.clan-sy.com/phpbb/viewtopic.php?p=193118#193118) and I keep coming up with errors when I attempt to compile.

```

checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 libglade-2.0    ) were not met:

No package 'libglade-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

I clearly have libglade2-0 installed:
```

isaac@isaaclw2:~/springlobby$ sudo apt-get install libglade2-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglade2-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
I tried [following advice in the Ubuntu Archives](http://ubuntuforums.org/archive/index.php/t-16727.html) but re-installing libgtk2.0-dev didn't help...

I also looked up the gtk+-2.0 error, and it took me to [another ubuntu archive](http://ubuntuforums.org/archive/index.php/t-448542.html). But this didn't really help either because I already have had gaim installed (and now pidgin).

Could someone help me with "adjusting the PKG_CONFIG_PATH environment variable" since that's what it seems to be asking about? I went around an installed alot of other libraries relating to [wxWidgets](http://www.wxwidgets.org/downloads/) since that was the program(?) that was supposed to help me compile.

---

### Post by 444 on 2007-06-09
Did you install libglade2-dev

---

### Post by cong06 on 2007-06-09
....no


guess that did it then.
Thanks.

---

