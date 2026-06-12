---
title: "gfontview or other font viewing program in intrepid"
date: 2008-09-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by durand on 2008-09-02
I'm not sure what happened to the font viewer but at the moment, there is no default way of viewing font files...I think gfontview used to be installed but it's not been in the repos since gutsy according to packages.ubuntu.com...

Is there an alternative to it? I just need a simple font viewer that does text preview when you double click on a font file. I use font matrix but it's not as fast to preview fonts.

Thanks

---

### Post by hugmenot on 2008-09-02
The default font viewer was just dropped. 

[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-control-center/+bug/216875](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-control-center/+bug/216875)

---

### Post by durand on 2008-09-02
Thats very annoying....We/I need a font viewer. Do you know if there are any plans to replace it? I didn't have any problems with the old one....

---

### Post by Cherry Cotton on 2008-09-03
I agree! I was really confused when I couldn’t find the font viewer. Sometimes, you just need a simple program that previews a font, just like how we have a document viewer and an image viewer. I hope this program gets put back in.

---

### Post by hugmenot on 2008-09-03
BTW, the bug I cited was only for your information. It is marked as invalid because it complained about wrong rendering.

Durand, will you open a new bug to point out the regression?

---

### Post by durand on 2008-09-03
Should I file it with gnome upstream or launchpad?

---

### Post by hugmenot on 2008-09-03
I'd say Launchpad in this case. Perhaps they can repackage gnome-font-viewer from an old release.

---

### Post by durand on 2008-09-03
[https://bugs.edge.launchpad.net/ubuntu/+source/meta-gnome2/+bug/264463](https://bugs.edge.launchpad.net/ubuntu/+source/meta-gnome2/+bug/264463)

---

### Post by Nullack on 2008-09-03
gucharmap was updated recently

---

### Post by durand on 2008-09-03
> **Nullack said:**
> gucharmap was updated recently

That's a character map, not a font viewer.

A font viewer would display the name of the font and relevant details like that as well as preview the font with "The quick brown fox jumps over the lazy dog" in different sizes

---

