---
title: "can't open zip/rar files"
date: 2010-02-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dino99 on 2010-02-11
recent problem when i want to dezip a file:

End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/oem/downl/setup.zip or
          /home/oem/downl/setup.zip.zip, and cannot find /home/oem/downl/setup.zip.ZIP, period.

very strange.

---

### Post by dino99 on 2010-02-11
some zip files can be opened but not all.

---

### Post by MacUntu on 2010-02-11
Works fine here. Can you upload an example?

---

### Post by dino99 on 2010-02-11
[attach]146748[/attach]

---

### Post by cecilpierce on 2010-02-11
> **dino99 said:**
> [attach]146748[/attach]

Don' know what your trouble is but you could try "Midnight Commander" it will do just about any thing you want.
sudo apt-get install mc and run it in a terminal as user to try it out, be careful if you run it as root!

---

### Post by dino99 on 2010-02-11
> **cecilpierce said:**
> Don' know what your trouble is but you could try "Midnight Commander" it will do just about any thing you want.
sudo apt-get install mc and run it in a terminal as user to try it out, be careful if you run it as root!

thanks, of course i know and still use this nice app, but here i post about problem with built-in Lucid's package (nautilus). Previous one work for me in all situations but not last one.

---

### Post by VMC on 2010-02-11
> **dino99 said:**
> thanks, of course i know and still use this nice app, but here i post about problem with built-in Lucid's package (nautilus). Previous one work for me in all situations but not last one.

How did you create that zip file? Just a simple compression or some added feature.

---

### Post by MacUntu on 2010-02-11
I can only find the file's "local file header" signature (0x04034b50)... you sure this isn't part of a multi-file archive? Can other apps extract it?

---

### Post by dino99 on 2010-02-11
well it's a file that i've downloaded so don't know much about it, i'll request an other one  ):P

thanks you all (nautilus is not broken)

---

### Post by seeker5528 on 2010-02-11
Setup.zip looks like it is not a zip file, so if all these archives you are having trouble with are downloaded from the same place, maybe there is something hinky going on on the other end.

Later, Seeker

---

