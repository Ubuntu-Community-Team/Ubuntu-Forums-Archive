---
title: "Upgrade from 8.10 to 9.04 final - file system"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by FX2908 on 2009-04-09
Hi there.

I've got one question. I currently have Ubuntu 8.10 installed and i want to upgrade to 9.04 when it's final. My doubt is, will the file system be automatically updated too (from ext3 to ext4)?

Thanks. :)

---

### Post by Stupendoussteve on 2009-04-09
It should not modify the filesystem, only the files on the filesystem. Changing the FS will probably take manual conversion.

---

### Post by Therion on 2009-04-09
I've done a couple clean installs of Jaunty and each time I had to *specifically* change the file-system *to* ext4 from the default ext3 option.

My point here being, ext4 is an OPTION in Jaunty (at least so far) not the default filesystem.

---

### Post by FX2908 on 2009-04-09
Hum, ok, i believe that answers my question. Thanks all.

---

