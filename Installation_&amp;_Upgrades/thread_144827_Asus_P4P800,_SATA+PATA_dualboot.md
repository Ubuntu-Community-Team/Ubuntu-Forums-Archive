---
title: "Asus P4P800, SATA+PATA dualboot?"
date: 2006-03-15
forum: Installation &amp; Upgrades
---

### Post by /dev/null on 2006-03-15
Hello,

I want to install (dualboot) Ubuntu 5.10 on my system to the PATA Drive:

Asus P4P800 deluxe, P4 3.2GHz 

[ICH5-Controller]
- 1 SATA Drive (WinXP installed)

[VIA VT6410 Controller]
- 1 PATA Drive
- 1 DVD-Drive
- 1 DVD-Burner

When I boot up the install CD, the installer only shows me the SATA drive for partitioning. But how is it possible to install it to the PATA drive and not the SATA?

The DVD-Drive (with the install disc) is recognized correct, but not the PATA HDD....

Every howto I found is for setting up RAID or SATA on this Mainboard but not anything for a setup like mine :-(

Any ideas/hints? :-k

---

### Post by timas on 2006-03-15
try doing the insall with noapic and or nolapic.. that might however, make the sata drive disappear alltogether for linux.. so:

boot the CD
do 'install noapic' OR 'install nolapic' OR 'install noapic nolapic'

Try them out, see where they take you :) I had to do both in order to even install it to a connected PATA drive, couldn't get far enough into the setup without doing both

---

### Post by /dev/null on 2006-03-15
I messed around with the settings, but nothing worked.

Sometimes it hangs on startup or the PATA drive isn´t recognized :cry: 

Any other ideas?

---

### Post by /dev/null on 2006-03-17
I solved the problem.....

There is a kernelpatch available to get the VIA chipset working: [http://source.robertk.com/](http://source.robertk.com/) 

or you need a kernel > 2.6.15-rc2 where the functionality of this patch is already included.

Now I´m running Dapper and everything´s fine \\:D/

---

