---
title: "ImageMagick not found"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by essell513 on 2008-08-29
I have just installed IM with Synaptic and although all the files are in the /usr folder, there is nothing showing when I click on Applications/Graphics. What have I done wrong or what have I not done?:(

---

### Post by Vivaldi Gloria on 2008-08-29
Imagemagick consists of the following (mostly) command line tools:

```
/usr/bin/animate
/usr/bin/compare
/usr/bin/composite
/usr/bin/conjure
/usr/bin/convert
/usr/bin/display
/usr/bin/identify
/usr/bin/import
/usr/bin/mogrify
/usr/bin/montage
/usr/bin/stream
```

See their man pages for more info, e.g. open a terminal and give the command

```
man stream
```

and press "q" to exit.

---

### Post by essell513 on 2008-08-29
Thank you; I don't think I'm quite ready for this level of usage - only just started. I think I'll stay with Gimp!

---

