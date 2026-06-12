---
title: "Texlive and Ubuntu -&gt; GUIs crash on latex-error"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by wamoz on 2010-08-03
Hi,
I have tried to compile a .tex file using pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian) on my kubuntu 10.04.
Manually, executing "latex", everything works. 
When I use a GUI like Kile or texmaker, it works, if there are no errors in the tex-file. 
If there is an error, the "latex" program hangs forever and Kile or texmaker hang then as well which is so annoying.
I rule out the possibility that it is a Kile oder texmaker problem, since both hang, so no more information on versions and so on for those is necessary.
The weird thing is, that manually executing the latex-command on the .tex file including an error works as well - it just complains that e.g. the graphics-file is not found or so.
The tex-file is okay, since on an older machine, which uses an older version of latex and kile, everything is fine as well.
Ah, I forgot - the log in Kile tells me the error, e.g. missing graphics file - and then it hangs and cannot recover.
Also, this only happens with a certain *.cls file - which I have to use and must not change. 
I assume I am making some ugly non-latex rooky mistake I just don't see right now... Googling the whole day did not show up any solution.
Thanks for any ideas.

---

