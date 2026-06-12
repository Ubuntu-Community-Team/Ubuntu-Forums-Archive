---
title: "Executing Files/programs"
date: 2012-01-13
forum: Installation &amp; Upgrades
---

### Post by stormshadow21 on 2012-01-13
I was trying to install flash player on my system and from time to time I have wondered how to execute extracted files through the terminal once i cd into the folder containing the file i want to execute and i just dont know where to go from there.

---

### Post by mikewhatever on 2012-01-14
To execute a file, type './file_name'. Note, it's not required to execute anything when installing Flash.

---

### Post by cortman on 2012-01-14
...And if the file gives a "permission denied" error instead of executing, you need to modify the file permissions-

```
chmod +x file_name
```

---

### Post by stormshadow21 on 2012-01-17
> **mikewhatever said:**
> To execute a file, type './file_name'. Note, it's not required to execute anything when installing Flash.
The how else do i install flash because i never seem to know how to do that either?

---

### Post by lykwydchykyn on 2012-01-17
I believe you can just install the "ubuntu-restricted-extras" package from the repositories.  That should cover flash an a multitude of other a/v codecs

---

### Post by oldos2er on 2012-01-17
[https://help.ubuntu.com/community/RestrictedFormats/Flash#A64_bit_Ubuntu](https://help.ubuntu.com/community/RestrictedFormats/Flash#A64_bit_Ubuntu)

Or Flash-Aid, a Firefox add-on (see my sig).

---

