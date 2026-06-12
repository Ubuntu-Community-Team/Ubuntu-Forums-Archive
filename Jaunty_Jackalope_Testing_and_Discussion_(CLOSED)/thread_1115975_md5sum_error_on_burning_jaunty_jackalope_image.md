---
title: "md5sum error on burning jaunty jackalope image"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by - 000 - on 2009-04-04
I tried to burn the jaunty beta image on three different burning programs, but they all give me the same error: the checksum is not the same

image on HDD: 
> 03b63dada5e5fce0119a52d822e406a1

Then I go into the terminal and type:
> md5sum /dev/cdrom
and I get:
> baa8505912d38c50f21ead25d563295b

---

### Post by Kareeser on 2009-04-04
The md5sum is supposed to be run on the CD image only. It doesn't correspond with the burned CD-ROM :)

---

### Post by - 000 - on 2009-04-04
huh

so it's fine then? :D

---

