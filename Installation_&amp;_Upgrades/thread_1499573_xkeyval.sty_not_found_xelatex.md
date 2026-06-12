---
title: "xkeyval.sty not found xelatex"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by vamega on 2010-06-02
Hi I'm trying to use xelatex to produce a pdf for a .tex file I have.
The tex file uses the fontspec package.

When I run xelatex it gives me this error.

```
! LaTeX Error: File `xkeyval.sty' not found.
```How can I fix this?

Thanks in advance

Vamega

---

### Post by vamega on 2010-06-02
I solved this with a little research on other packages.
I think there is a bug with this package, because I think this file is supposed to have been included by default.

Nevertheless, to solve this what I did what download xkeyval.zip from [http://tug.ctan.org/search.html](http://tug.ctan.org/search.html). I extracted the contents of the run folder of the archive root to /usr/local/share/texmf

then ran ```
sudo texhash /usr/local/share/texmf.
```

I for the most part simply modified this solution

[http://ubuntuforums.org/showthread.php?t=1447342](http://ubuntuforums.org/showthread.php?t=1447342)

---

### Post by Gorgapor on 2010-08-12
I solved it like this:

```

$ apt-cache search xkeyval
texlive-latex-recommended - TeX Live: LaTeX recommended packages
$ sudo apt-get install texlive-latex-recommended

```

---

