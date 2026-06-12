---
title: "LaTex Package install after Ubuntu 10.04 upgrade"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by virsto on 2010-06-12
I recently upgraded to Unbuntu 10.04 and everything went well --- almost. When I tried to use LaTex I found that one of my style files was no longer present. 

Before the upgrade to 10.04, the package arydshln was in /usr/texmf-texlive/tex/latex/myclsstyfiles. But now it is missing (no where on my computer!) 

I believe that this can be fixed if someone could tell me how to  download and install a specific LaTeX package, in this case -- arydshln (available at  CTAN). Note, I am using Texmaker.

Thank you

---

### Post by virsto on 2010-06-12
I found a solution:

These are the steps that I used:
1. Saved my old environment file as environment_old (just in case...)
2. Used  	Code:
 	sudo chmod 777 environment 
 to allow full access to environment
3. Used Gedit to change environment to:

 	Code:
 	PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/share/texmf-texlive/tex/latex" 
4. Used  	Code:
 	sudo chmod 644 environment 
 to restore the original attributes to environment.

And Texmaker now works as it should --- finds my *.sty and *.cls files  in folders in .../latex.

Thanks again darko and have a good day (well it is actually is 01:19  Sunday **morning** here in Stockholm).

--V

---

