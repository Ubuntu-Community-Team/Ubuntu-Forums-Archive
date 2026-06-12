---
title: "problem installing udunits"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by Jaques on 2010-01-13
Hello, everybody!

I'm trying to install udunits on Karmic, using the advices from an older thread in the archives: [http://ubuntuforums.org/showthread.php?t=120241]("http://ubuntuforums.org/showthread.php?t=120241")

When running *make test* I get the following output:
```

making `test' in directory /home/jaques/downloads/udunits-1.12.9/src/udunits

make[1]: Betrete Verzeichnis '/home/jaques/downloads/udunits-1.12.9/src/udunits'
make[2]: Betrete Verzeichnis '/home/jaques/downloads/udunits-1.12.9/src/udunits'
gcc -c -O -I../lib -I../port/misc -Df2cFortran udunits.c
udunits.c: In Funktion »main«:
udunits.c:116: Warnung: Unverträgliche implizite Deklaration der eingebauten Funktion »exit«
make[2]: *** Keine Regel vorhanden, um das Target »../lib/libudunits.a«, 
  benötigt von »udunits«, zu erstellen.  Schluss.
make[2]: Verlasse Verzeichnis '/home/jaques/downloads/udunits-1.12.9/src/udunits'
make[1]: *** [program] Fehler 2
make[1]: Verlasse Verzeichnis '/home/jaques/downloads/udunits-1.12.9/src/udunits'
make: *** [udunits/test] Fehler 1

```

I think in english this would mean something like
```

udunits.c:116: Warning: Incompatible implicit declaration of built-in function »exit«
make[2]: *** No rule to make target »../lib/libudunits.a«
```

Does anyone have an idea how to solve this?

Thanks, Jaques

---

### Post by gsmanners on 2010-01-13
Any particular reason you're using that really old version? I just built v2.1.12 no problem here.

---

### Post by Jaques on 2010-01-13
I wanted to install the package "RNetCDF" in R, which needs udunits and seems not to work with udunits-2.

For me, it doesn't matter anymore since I found out that there is another R-package for netcdf-support in R (called "ncdf"). Should I set the thread to "solved"?

thx, Jaques

---

