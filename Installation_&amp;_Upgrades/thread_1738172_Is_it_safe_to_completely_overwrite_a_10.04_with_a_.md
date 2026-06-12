---
title: "Is it safe to completely overwrite a 10.04 with a 11.04? (worried for grub)"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by balta on 2011-04-24
Hi there,
First of all: **HAPPY EASTER EVERYONE!**
Back on topic now.
Here's the scenario: I've got a netbook which *dual boots ubuntu and windows xp using grub legacy*.
Now I'd like to *overwrite my current ubuntu 10.04 installation with a brand new 11.04*.
Grub is my main preoccupation: I'm worried installing 11.04 over the old installation may cause quite a mess due to the two grubs not going along well.
My *question* is:
Is it safe* to overwrite the older ubuntu installation with the new using the "traditional" bootable USB method?

*safety includes windows accessibility and data preservation.

Sorry if my question is silly: I don't really understand how does grub work.
Sorry if my question was already asked: if this is the case please point me to it.

Thanks for your attention and happy easter again!

---

### Post by wojox on 2011-04-24
It's safe. Grub2 will be written to your MBR and grub legacy will not reside any where. Grub2 will pick up Windows as well.

---

### Post by balta on 2011-04-24
Dear wojox,
thanks for your extremely quick, precise and comforting reply.
Once again happy easter.
Thanks.
<3

---

