---
title: "TeXLive 2007 LaTeX in Feisty -- help"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by shaviro on 2007-04-24
The TexLive 2007 installation of LaTeX worked fine under Edgy. I just installed Feisty, however, and now LaTeX no longer works. 

When I try to process a TeX file I get the following:

```
This is pdfeTeX, Version 3.141592-1.30.5-2.2 (Web2C 7.5.5)
kpathsea: Running mktexfmt pdflatex.fmt
mktexfmt: no info for format `pdflatex'.
I can't find the format file `pdflatex.fmt'!
```

Now, in fact I do have the pdflatex.fmt file on my system:

```
shaviro@Naufana:~$ locate pdflatex.fmt
/home/shaviro/.texlive2007/texmf-var/web2c/pdftex/pdflatex.fmt
```

But kpathsea cannot find it, because the relevant directory is not in its search path:

```
shaviro@Naufana:~$ kpsewhich -show-path="fmt"
.:/home/shaviro/.texmf-config/web2c:/home/shaviro/.texmf-var/web2c:/home/shaviro/texmf/web2c:/etc/texmf/web2c:!!/var/lib/texmf/web2c:!!/usr/local/share/texmf/web2c:!!/usr/share/texmf/web2c:!!/usr/share/texmf-texlive/web2c:!!/usr/share/texmf-tetex/web2c
```

So, how do I rectify this situation? How can I get the right directory into kpathsea's search path, so that I can run pdflatex properly?

Thanks for any help. Not being able to run LaTeX, I am totally crippled.

---

### Post by shaviro on 2007-04-25
Please ignore. My stupidity. I neglected to include the newly installed TeX commands in my $PATH, and that is why I was having the troubles I described. Once I corrected the $PATH, everything works as it is supposed to.

---

### Post by cmf on 2007-05-26
shaviro-

This is late but rather than start a new thread...

I have a similar puzzle where I had Edgy and TeXLive2005 working fine. Upgraded to Feisty but now I cannot successfully run the TeXLive2007 sudo install-tl.sh because it appears there are permission issues 

"/bin/tar: texmf-dist/doc/latex/graphics/keyval.pdf: Cannot stat: Permission denied"

for thousands of files...did you face this or what might I be missing (too much reliance on sudo?)

thanks if you get to this.

cmf

---

