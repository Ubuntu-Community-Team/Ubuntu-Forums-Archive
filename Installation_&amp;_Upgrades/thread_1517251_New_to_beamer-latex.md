---
title: "New to beamer-latex"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by kunda on 2010-06-24
Hello,

I am a regular user of latex but I have never used it for presentations; I was told to download latex-beamer; I am not sure I am doing it correctly because I have downloaded beamer but it still is not working. I wonder if I need to look for a specific class under beamer and save it in the same folder as my presentation; 

I am a bit confused and needs help....

Kunda

---

### Post by Stefan_K on 2010-06-28
Hi Kunda,

downloading and installing latex-beamer should be sufficient. Perhaps run texhash or [mktexlsr]("http://texblog.net/hypertext-help/latex-tools/mktexlsr/"):
```
sudo texhash
```
at the command prompt, it might help.

Stefan

---

### Post by kunda on 2010-06-28
Thank you very much Stefan; it has worked now. Many thanks.

Kunda

---

### Post by kalwisti on 2010-06-28
Hi, kunda,

For a gentle introduction to beamer, you might want to take a look at this article from the *PracTeX Journal*:

[http://www.tug.org/pracjourn/2005-4/mertz/](http://www.tug.org/pracjourn/2005-4/mertz/)
Mertz, Andrew, and William Slough. "*Beamer by Example*." 

The *PracTeX Journal* publishes (typically) brief articles geared towards new-to-intermediate LaTeX users. I've found some very helpful information there.

---

