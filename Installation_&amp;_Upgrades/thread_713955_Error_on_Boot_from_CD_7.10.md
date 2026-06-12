---
title: "Error on Boot from CD 7.10"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by Bonanzaman on 2008-03-03
*Attempting to boot from live CD (purchased, not downloaded cd) and getting:*

(initramfs)   [82.231234]     ata1.0: exception Emask 0x0 Sact 0x0 SErr 0x0 action 0x2 frozen

*then......repeated 4 ot 5 times then:*

Buffer I/O error on device Sda, logical Block 0
      "                             "                                 1
       "                            "                                 2
           "                               "                          3
 *ect, thru *                                                       7

*Any insight here? Thanks!!!!*

---

### Post by dstew on 2008-03-03
Usually this means there is some hardware problem. Do a Memory Test from the Live CD first menu, and check the CD integrity also.

---

### Post by Bonanzaman on 2008-03-03
Thanks,....... I popped the CD into my work computer and it runs just fine....so no disc errors I'd guess. Where's the best place to start looking for the possible hardware issue ?

---

### Post by Ganymedes on 2008-03-03
Perhaps Ultimate Boot CD would be a place to start. That gives you a bunch of all kinds of utilities. Just Google for it. That also makes it possible to boot - any OS for that matter - from a CD, when booting from a CD otherwise does not even begin to work. Your problem does not really seem to fall into the latter category, but it might - easy to check.

---

### Post by Bonanzaman on 2008-03-03
Thanks for the UCD suggestion......got it, and I'm running the memory checks now, and will try em' all ! Bloody slow , though!

---

### Post by Bonanzaman on 2008-03-03
Memory checks OK, but upon READING the sys requirements, I find that while only 256M is necessary to run Gutsy when installed on the system, .... when running from the CD directly, 384M is the minimum !

Looks like we'll  need to install some more memory, and try again!

---

### Post by Bonanzaman on 2008-03-10
Well, added another 256M for a total of 384M, tried again, no Joy!....
some additional lines which I did not record before:

[81.231234]  ata1.00 cmd C8/00:08:00:00:00:00:001e0 tag 0 cdb 0x0
data 4096 in

Of course none of this has any meaning to me....is there a resource for looking up error codes with this O/S, so I might have some hope of being able to use it........ someone previously suggested a hardware issue. I'm wondering how to find out without randomly replacing hardware to find the problem!  Help?

---

