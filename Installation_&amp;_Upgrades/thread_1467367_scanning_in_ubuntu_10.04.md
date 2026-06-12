---
title: "scanning in ubuntu 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by rjfallis on 2010-04-30
I've just upgraded. and my scanner epson 3170. just won't work, I've reinstalled xsane. but none of the scanner programs will see the scanner, they all just say scanner not found,
help? does anyone have any ideas

bob

---

### Post by dbum on 2010-05-01
Mine didn't work either after the upgrade :(
I have a Brother 5440CN and I uninstalled all of the drivers for it and reinstalled them

Here are the packages I reinstalled

brscan2-0.2.5-1.i386.deb      
cupswrapperMFC5440CN-1.0.2-3.i386.deb
brscan-skey-0.2.1-3.i386.deb  
mfc5440cnlpr-1.0.2-1.i386.deb

and now everything works great....
Hope this helps

P.S. Try out Simple Scan that comes with 10.04... I like it better than xsane

---

### Post by liferfe on 2010-05-10
I have the same problem with Epson 3170 and Ubuntu 10.04 (after upgrading from 9.04 - 9.10): SimpleScan just doesn't see it, and I can't use it with Gimp-XSane.

I've found a transitional solution at an italian forum:
  1. Open a terminal
  2. Write "gksudo xsane" 
  3. A warning appears about using XSane as a root, confirm.

Then, in my case XSane opens and see the Epson 3170.

I hope somebody find a better way to use it.

---

### Post by eexcellent on 2010-05-19
I have the same setup as you liferfe, gksudo xsane doesn't work for me.
I now have an a4 paperweight :(

---

