---
title: "Subpixel font rendering"
date: 2008-09-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by _oOMOo_ on 2008-09-08
I'm using the Nvidia 170.70 driver and have checked subpixel rendering in appearances, and all the characters on the screen have a distinct red edge to them. It's not awful but it's worse than in Hardy.

Does anyone know if this is an X or font issue, or a setting in Compiz or Nvidia?

Cheers

Edit: Bug already submitted [here]("https://bugs.launchpad.net/ubuntu/+source/cairo/+bug/264254")

---

### Post by forumache on 2008-09-08
I have the same problem, although for a while, after an update where it fixed something "we have bitencoder disabled, it is not more evil than... i don't remember exactly the text from changelog" I had perfect rendering of characters.

Then, after 1-2 weeks, it is completely wrong, I disabled LCD pixel subrendering option in appearence|fonts

I have nvidia too, I don't know if the problem is nvidia related

---

### Post by psyke83 on 2008-09-08
Discussion of these issues on the forum can be a waste. At the very least, be sure to check if a bug exists, and file one if necessary.

Here's your bug, by the way: [https://bugs.launchpad.net/ubuntu/+source/cairo/+bug/264254](https://bugs.launchpad.net/ubuntu/+source/cairo/+bug/264254)

---

### Post by _oOMOo_ on 2008-09-08
Thanks for the heads up on the bug, I would normally have expected to see some discussion in the forum about this issue but a search showed nothing...

From the sticky post "Contributing to Intrepid"

"Whenever you encounter a reproducible malfunction in Intrepid, file a bug report. It's a good idea to start a thread in the development forum before submitting your report, to discuss it with others who may have experienced it, to make sure it's genuine."

---

### Post by vikrant82 on 2008-09-08
I had really been struggling collecting ppl's fonts folders and wondering what's wrong. 

Before stumbing on this thread, I had 10 fonts confguration with all modified files and still that crappy terrible looking font.

For now downgrading to libcaro2 1.6.4 helps.

---

