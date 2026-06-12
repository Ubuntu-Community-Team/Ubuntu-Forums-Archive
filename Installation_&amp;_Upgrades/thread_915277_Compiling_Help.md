---
title: "Compiling Help?"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by Dylnuge on 2008-09-09
So, I was following some instructions for compiling something, and I got this error during ./configure:

```
configure: error: libxml2 development files not found, XML won't be supported.
This is an error since --with-xml was requested.
```

No problem, I check with aptitude, and sure enough, libxml2 has an update, and libxml2-dev isn't installed. I update the first, install the second, and run the ./configure again.

Again the error occurs. I try rebooting, and it's still there.

Any suggestions or ways I can fix this?

Thanks,
Dylan

---

### Post by Partyboi2 on 2008-09-09
If you dont need xml support maybe you could compile without it
```
./configure --without-xml
```
What program are you trying to compile?

---

### Post by IllegalCharacter on 2008-09-09
Maybe try reinstalling libxml2-dev through Synaptic. I have had weird things happen when installing stuff with aptitude.

---

### Post by tuxxy on 2008-09-09
Maybe when you ./configure you could try to configure with xml and point to the location of the dependant files.

---

### Post by cariboo on 2008-09-09
Delete the **config.log** file and try it again.

Jim

---

