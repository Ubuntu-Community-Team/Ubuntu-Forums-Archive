---
title: "htk problem [+2319]"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by bejimed on 2012-03-22
After installing htk 3.4.1 on my ubuntu system, i try to exexute this command 
HERest -C config -C config.global -S adapt.scp -I adaptPhones.mlf -H hmm9/macros -u a -H hmm9/hmmdefs -z -K xforms mllr1 -J classes -h '*/%%%%%%_*.mfc' monophones1

but i have a big problem : 
RROR [+2319]  HERest: output TMF file expected
 FATAL ERROR - Terminating program HERest

my config.global file contain these elements : 

HADAPT:TRANSKIND = MLLRMEAN
HADAPT:USEBIAS = TRUE
HADAPT:BASECLASS = global
HADAPT:ADAPTKIND = BASE
HADAPT:KEEPXFORMDISTINCT = TRUE

HADAPT:TRACE = 61
HMODEL:TRACE = 512

---

