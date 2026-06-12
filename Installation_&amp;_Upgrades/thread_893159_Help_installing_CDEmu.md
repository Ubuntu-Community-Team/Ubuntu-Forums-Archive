---
title: "Help installing CDEmu"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by dargonknf on 2008-08-18
I need help installing CDEmu.  When I run "./configure" after having moved to the correct directory the command gives me this error: "No package 'pygtk-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables pygtk_CFLAGS
and pygtk_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details." after running.

Can anyone explain to me what I'm doing wrong and how to fix it?

Thank you in advance for your help.

---

### Post by Partyboi2 on 2008-08-18
Try installing the python-gtk2-dev package[FONT=monospace]
[/FONT]```
sudo apt-get install python-gtk2-dev
```

---

### Post by dargonknf on 2008-08-19
Ok, THanks. I did that and I can now run "./configure" but when i run the "make command it gives me another error:
"Making all in pixmaps
make[1]: Entering directory `/home/pif/Desktop/gcdemu-1.1.0/pixmaps'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/pif/Desktop/gcdemu-1.1.0/pixmaps'
Making all in po
make[1]: Entering directory `/home/pif/Desktop/gcdemu-1.1.0/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[1]: *** [de.gmo] Error 127
make[1]: Leaving directory `/home/pif/Desktop/gcdemu-1.1.0/po'
make: *** [all-recursive] Error 1"
Does anyone know what I'm doing wrong here and willing to explain?
Again thanks in advance for the help.

---

### Post by Partyboi2 on 2008-08-20
Have you thought about installing the deb package of the program? You can install that from [[COLOR=Blue]here[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=93175") It is alot easier then trying to compile.

---

### Post by dargonknf on 2008-08-20
And that was a lot easier, Thank you again

---

