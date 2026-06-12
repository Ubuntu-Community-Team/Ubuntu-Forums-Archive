---
title: "xsane won't believe I have an Epson allinone"
date: 2017-12-14
forum: MINT
---

### Post by jamzen on 2017-12-14
When I try to scan something from my Epson WF-3640 all-in-one, xsane comes up telling me that it found an HP8610.  This is under Mint18.2, with xsane 0.999.
On the same host, I can also boot up Mint17.3, running xsane 0.998, and which can find the WF-3640.

I just installed *a fresh mint18.3 on a clean partition, installed xsane, and it told me my printer was an HP Officejet 8610*.

How can this happen in a virginal installation?  Anybody?

---

### Post by DuckHook on 2017-12-15
*Thread moved to **MINT** as the more appropriate forum.*

---

### Post by pdc on 2017-12-15
so Mint has its own forums; if you wish to ask there for Mint things ; [https://forums.linuxmint.com/](https://forums.linuxmint.com/)

I think Epson would suggest you install the drivers they offer for the WF-3640; the imagescan file they offer covers a wide range of their devices [http://support.epson.net/linux/en/iscan_c.php?version=1.0.4](http://support.epson.net/linux/en/iscan_c.php?version=1.0.4) and you will likely need the [COLOR="#0000FF"]iscan-bundle-1.0.4.x64.deb.tar.gz[/COLOR] and if you click to download that; and select OPEN, then gdebi installer should leap in and offer to install it for you; that should create a programme called [COLOR="#FF0000"]ImageScan[/COLOR] that you will find in your Graphics folder; or just use DASH .... and it should drive the scanner for you

---

