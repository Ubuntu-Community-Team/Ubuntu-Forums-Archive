---
title: "Places menu behavior (Alpha 6 live CD)"
date: 2008-09-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by QwUo173Hy on 2008-09-19
Just booted up the alpha 6 and the behavior of the Places menu seems inconsistent to me.

Clicking on Home, Desktop, Music ... Computer, CD Creator, Network etc. all bring up a file browser. However, my other internal harddrives do not appear when I click on them. I did discover that the icons were placed on the desktop but the window should really be opened as well.

If I have a web browser opened for example, I may not notice these icons. Also, I am sure that the average user intends on eventually browsing these filesystes!

Does this justify a bug report?

---

### Post by Nullack on 2008-09-19
Are you sure you were not mounting the drives?

---

### Post by Bou on 2008-09-19
I think you might be talking about this bug I opened: [https://bugs.launchpad.net/nautilus/+bug/269901](https://bugs.launchpad.net/nautilus/+bug/269901)

---

### Post by QwUo173Hy on 2008-09-19
> **Nullack said:**
> Are you sure you were not mounting the drives?

Yes, the result is that the drives were mounted. But I would have expected a window to open also just like any other entry in the Places menu. Mounting should really be transparent to the user. The average joe just wants the thing to open so he can have a 'look-see'.

Bou, that is exactly the problem I'm describing. Glad to see it has been forwarded upstream!

---

### Post by Nullack on 2008-09-19
Agreed, usability issue, should happen in one process

---

