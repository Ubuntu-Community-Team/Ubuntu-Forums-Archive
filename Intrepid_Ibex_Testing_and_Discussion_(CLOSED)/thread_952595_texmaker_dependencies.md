---
title: "texmaker dependencies"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by thomasmayer on 2008-10-19
Hello everyone!

I tried to install texmaker (a latex editing environment), however it requires a lot of dependencies, resulting in a 348 MB download and 711 MB disk usage. Isn't that a bit much just for latex.

Regards,
Thomas

---

### Post by LinuxRofler on 2008-10-19
For mac os x it can be as much as 1 gig.

---

### Post by ssam on 2008-10-19
latex is huge if you install all the packages.

texmaker recommends texlive-latex-extra. now recommended packages get installed by default, so it will pull more packages then it used to.

possibly some of the 'recommends' should be demoted to 'suggests'

---

### Post by thomasmayer on 2008-10-19
Thank you for pointing me into the right direction, I didn't know about the automatically installed recommendations and now installed texmaker without them.

The texmaker package doesn't only recommend the texlive-latex-extra, but also tetex-extra which again depends on every texlive-lang-* package.

---

