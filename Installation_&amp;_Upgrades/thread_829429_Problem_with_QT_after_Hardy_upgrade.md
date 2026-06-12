---
title: "Problem with QT after Hardy upgrade"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by donatherton on 2008-06-14
After upgrading from Gutsy to Hardy, I found a problem with QT applications. The fonts appear garbled, looking like mathematical equations. See the attachment for a screenshot.

Any ideas?

Well, I should've guessed it was a simple solution! I opened qtconfig-qt4, and set the font to something other than 'sans-serif'. There appears to be some bug that affects font rendition of some fonts.

---

