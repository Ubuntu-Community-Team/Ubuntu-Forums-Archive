---
title: "can't paste in the / folder"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by AmirM on 2010-01-19
It may be funny and the answer might be very simple but...I dont know how to do that.
I cant paste thing into the / folder.I need to extract an archive into /opt for installing LAMPP.with "File roller" I get the message:
```

You don't have the right permissions to extract archives in the folder "file:///opt"

```

---

### Post by Xog on 2010-01-19
type sudo -i

then try again

---

### Post by erfahren on 2010-01-19
> **AmirM said:**
> It may be funny and the answer might be very simple but...I dont know how to do that.
I cant paste thing into the / folder.I need to extract an archive into /opt for installing LAMPP.with "File roller" I get the message:
```

You don't have the right permissions to extract archives in the folder "file:///opt"

```
you need administrative privileges (or "root privileges" as it's referred to) to do anything in the root file system.

A way around that using GUI apps is to open Nautilus (the default Ubuntu file browser) with root privileges, but be VERY careful with what you do!

to do that open up the run dialog by pressing ALT+F2 and type in:
```

gksu nautilus

```

---

### Post by AmirM on 2010-01-20
]I said thats simple,didnt I?
this worked.
```
sudo nautilus 
```

---

### Post by Cheesemill on 2010-01-20
To install LAMP you can just do:
```
 
sudo tasksel install lamp-server

```Doing it this way will make sure that it is kept updated.

---

