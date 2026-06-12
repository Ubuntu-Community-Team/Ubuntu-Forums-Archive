---
title: "Karmic &amp; MESA 7.6 &amp; Gallium3D &amp; ATI R500 series cards"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by frogotronic on 2009-09-24
Hello,

  Check me on this - the new MESA drivers (7.6) included with Karmic should contain the Gallium3D code and therefore enable proper 3D rendering using open source radeon/radeonHD/mesa drivers on the R500 series ATI cards that were dropped from the proprietary FGLRX support (catalyst 9.3)?

Yes/No?

- Thanks

---

### Post by barisurum on 2009-09-26
I think not cement_head. Yes it is true that mesa 7.6 contains Gallium3D code, but this code is not active as far as I know. Neither the core gallium3d driver for r300- r500 radeon chipsets nor feature supports for 2d EXA acceleration and opengl 1.3-2.1 are not mature yet. You may check this with the xorg's radeonfeature tables: [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

I think the code is integrated for testing and development purposes only. Meanwhile the opensource radeon drivers consist of xorg's radeon driver.

---

### Post by frogotronic on 2009-09-26
> **barisurum said:**
> I think not cement_head. Yes it is true that mesa 7.6 contains Gallium3D code, but this code is not active as far as I know. Neither the core gallium3d driver for r300- r500 radeon chipsets nor feature supports for 2d EXA acceleration and opengl 1.3-2.1 are not mature yet. You may check this with the xorg's radeonfeature tables: [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

I think the code is integrated for testing and development purposes only. Meanwhile the opensource radeon drivers consist of xorg's radeon driver.

Hi Barisurum,

  Thanks - I'll check it out, but makes sense.

- CH

:guitar:

---

