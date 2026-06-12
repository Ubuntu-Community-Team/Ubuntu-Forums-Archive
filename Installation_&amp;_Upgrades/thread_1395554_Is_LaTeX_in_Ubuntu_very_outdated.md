---
title: "Is LaTeX in Ubuntu very outdated?"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by Abdus on 2010-02-01
I use Ubuntu 9.10. A few days ago I installed TeX on my freshly upgraded Ubuntu 9.10 to work with some documents I made before using MiKTeX (Windows Vista). TeX kept announcing numerous errors - strange, as in MiKTeX all went ok. After check it occured that some classes I use are even a few years old in Ubuntu:
- 'memoir' version was from 2005 (!), and this class is constantly being updated and is available on CTAN (newest is January 2010),
- 'pgf' was old too.
Is it 'normal' or is something wrong with my installation? Is manual update of every single package I use the only option in this situation?

Thanks for any info/help.

---

### Post by rafita on 2010-02-01
yes, the last version of texlive in the official repositories seems to be 2007. You could download and install newest versions of packages in ~/texmf, that's what I do. But if you are adventurous, you could use Ailurus, which offers the option of installing texlive 2009 (I haven't tried that).

---

### Post by Abdus on 2010-02-01
Thanks for the tip. Tried Ailurus, seems a handy application.

Right now I didn't spot any problems, TeX works as it used to, not sure if it noticed all the new files or not. Will have to figure it out soon. :)

---

