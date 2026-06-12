---
title: "Haven't found yet - How to change scren font of GRUB2 display?"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-12
Thanks.

---

### Post by MacUntu on 2009-10-12
Open the font (I only tested this with the psf format) you want to use with gbdfed, convert it to a bdf file (open, import, save as) and then use grub-mkfont to generate a pf2 file - something like```

grub-mkfont --output=output.pf2 input.bdf
```

If you don't want to edit GRUB's config files, simply replace /usr/share/grub/unicode.pf2 with your file (don't forget to backup the original unicode.pf2 file).

**Edit**: made some changes due to outdated information.

**Edit 2**: another thing's different now - above should finally work (just tested it). :D

---

