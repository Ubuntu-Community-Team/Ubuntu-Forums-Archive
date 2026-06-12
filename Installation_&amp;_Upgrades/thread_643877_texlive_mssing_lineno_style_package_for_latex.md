---
title: "texlive mssing lineno style package for latex"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by alvenegas on 2007-12-18
A couple of days back I upgraded my 64-bit machine from edgy to gutsy via a fresh install (the upgrades were a total mess).  While working on a latex file that required the package lineno.sty, I realized that texlive distribution does not have it.  I therefore, went for looking for the file and found it on CTAN.  However, after installing it in the correct directory:
/usr/share/texmf-texlive/tex/latex/
the compiler would not find it, even when all the permissions were correct.  In order for latex know that a new package has
been installed, the command "sudo texhash" needs to be invoked in order for
files in /var/lib/texmf be refreshed and reflect that a new package has been installed. Latex search these files instead of going through the actual directories, which results in a faster performance.

Hope this work and save many a couple of hours of frustration.

---

### Post by hugmenot on 2007-12-19
It would be wise to install local files into a local TEXMF tree, i.e., not under /usr/share/texmf.

You could use ~/texmf, for example. run "texhash" inside that, too.

---

### Post by ItalOz on 2008-01-16
I've the same proble
I've downloaded the package and put into the directory
TEXMFLOCAL=/usr/local/share/texmf
which did not existed, so I made it.
Then I run
latex package-name.ins and I have created the file
package-name.sty

But Kile does not see it even after I've tried running texhash in the directory and also texconfig (I always was always sudo)

It makes a file ls-R but does not seem to use it.

If I copy the file package-name.sty into the directory where my Tex files are the package works...

What am I doing wrong?

---

### Post by hugmenot on 2008-01-16
I don't know for sure, but maybe replicating the TEXMNF tree under /usr/local/share/texmf works. That means, make a directory /usr/local/share/texmf/tex/latex/package-name/ and put package-name.sty in there. Then run "sudo texhash".

With "kpsewhich package-name.sty" you can confrm that the file is findable.

---

### Post by TMW on 2008-07-15
Hi - I just found that the lineno style is in the texlive-humanities package. aptitude install texlive-humanities makes it conveniently available

---

