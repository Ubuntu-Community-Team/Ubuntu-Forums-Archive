---
title: "Gnome Guitar"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by Benchamoneh on 2010-02-23
Ok I've done a bit of searching around but can't find anything on this so it's time to ask in the forum. I'm trying to install Gnome Guitar from source but I keep getting the error message;

```
error CS0006: cannot find metadata file `Mono.Posix'
```

The source configures ok (after installing mono-mcs) but I get this error when running make. I'm not really sure what it's referring to and Googling it doesn't help.

Does anyone use Gnome Guitar? If so did you encounter this error and find some magical way of fixing it? Google returns very little and I can't even find contact details of the author from their website or the source code. Any help here?

---

### Post by Benchamoneh on 2010-02-25
If no one has any idea on how to fix this then could anyone at least suggest an alternative?

---

### Post by Benchamoneh on 2010-02-25
OK, installing libmono-posix1.0-cil progresses the problem slightly further. I reran ./configure and when making I know get the following error
```

System.IO.FileNotFoundException: Could not load file or assembly 'Mono.Cairo, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
```

I've attached the full make output in case it helps. I'm assuming this is some sort of conflict between the posix1.0-cil and posix2.0-cil packages? Maybe I should write this one off as a bad job?

---

### Post by jahLux on 2010-05-04
Try this :
[http://gnome-chord.sourceforge.net/#news](http://gnome-chord.sourceforge.net/#news)

---

