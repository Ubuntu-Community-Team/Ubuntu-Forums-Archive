---
title: "printing: kdeprint, xpp, gtklp?"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by mfriendly on 2011-04-01
[Not sure if this is the right forum; if not let me know.]
I have a new kubuntu 10.04 workstation, replacing an old debian system that died, and very little support from our IT group.

On the old system I had kprinter that allowed me to control details-- double sided, 4-up, etc. of print jobs from all my apps (xpdf, editors, etc.), but that it not installed, and aptitude search kdeprint shows nothing.

I'm not sure what to install to give me back this capability -- xpp?  gtklp? etc.

---

### Post by mfriendly on 2011-04-04
No one replied, so I tried installing xpp.  Now, I view a .pdf file with xpdf, click on print, then enter xpp
into "Print with command"
The xpp panel pops us, but nothing prints ...

Can someone help sort this out?

Console shows:


euclid: tex/scs % xpdf VCD-Workshop.pdf &
[1] 2200
euclid: tex/scs % *** glibc detected *** xpp: free(): invalid pointer: 0x00000000022b5a44 ***
======= Backtrace: =========
/lib/libc.so.6(+0x775b6)[0x7f2afe9345b6]
/lib/libc.so.6(cfree+0x73)[0x7f2afe93ae83]
xpp[0x40d7af]
xpp[0x406127]
/usr/lib/libfltk.so.1.1(_ZN8Fl_Menu_6pickedEPK12Fl_Menu_Item+0x9a)[0x7f2aff447a1a]
/usr/lib/libfltk.so.1.1(_ZN9Fl_Choice6handleEi+0x106)[0x7f2aff429a86]
/usr/lib/libfltk.so.1.1(_ZN8Fl_Group6handleEi+0x12b)[0x7f2aff43622b]
======= Memory map: ========
00400000-0041a000 r-xp 00000000 08:12 12007909                           /usr/bin/xpp
0061a000-0061b000 r--p 0001a000 08:12 12007909                           /usr/bin/xpp
0061b000-0061d000 rw-p 0001b000 08:12 12007909                           /usr/bin/xpp
0061d000-0061e000 rw-p 00000000 00:00 0 
022ab000-023d0000 rw-p 00000000 00:00 0                                  [heap]
7f2af4000000-7f2af4021000 rw-p 00000000 00:00 0 
7f2af4021000-7f2af8000000 ---p 00000000 00:00 0

---

