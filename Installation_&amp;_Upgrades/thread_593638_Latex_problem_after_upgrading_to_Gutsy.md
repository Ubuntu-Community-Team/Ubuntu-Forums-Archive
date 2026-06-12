---
title: "Latex problem after upgrading to Gutsy"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by skiold on 2007-10-27
I've been working with Latex very well in feisty, but I've decided to upgrade to Gutsy, everything works good except a little bug I've found when I was trying to modify my Latin works in Latex.
Before upgrading my Latin documents didn't have this trouble, and I hadn't done any change to my Latex preambles. After the upgrade this is the log message:

[I](/usr/share/texmf-texlive/tex/latex/base/latin1.def
File: latin1.def 2006/05/05 v1.1b Input encoding file
))
(/usr/share/texmf-texlive/tex/generic/babel/babel.sty
Package: babel 2005/11/23 v3.8h The Babel package

(/usr/share/texmf-texlive/tex/generic/babel/latin.ldf
File: latin.ldf 2005/11/17 v2.0g Latin support from the babel system

(/usr/share/texmf-texlive/tex/generic/babel/babel.def
File: babel.def 2005/11/23 v3.8h Babel common definitions
\babel@savecnt=\count87
\U@D=\dimen103
)
! Undefined control sequence.
l.184 \addtoextraslatin
                       {\LatinMarksOff}
The control sequence at the end of the top line
of your error message was never \def'ed. If you have
misspelled it (e.g., `\hobx'), type `I' and the correct
spelling (e.g., `I\hbox'). Otherwise just continue,
and I'll forget about whatever was undefined.

! Undefined control sequence.
l.184 \addtoextraslatin{\LatinMarksOff
                                      }
The control sequence at the end of the top line
of your error message was never \def'ed. If you have
misspelled it (e.g., `\hobx'), type `I' and the correct
spelling (e.g., `I\hbox'). Otherwise just continue,
and I'll forget about whatever was undefined.
[/I]
 

Any idea how to solve this bug? :confused:

---

### Post by pierref on 2008-02-22
Same problem here.

I wonder if you have found the way to fix this. My workaround is to hit the ENTER key twice after the warnings and the produced document seems to be OK, but I feel this is a rather unelegant solution.

---

