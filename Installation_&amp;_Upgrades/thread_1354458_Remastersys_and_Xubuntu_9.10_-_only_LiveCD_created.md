---
title: "Remastersys and Xubuntu 9.10 - only LiveCD created"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by babarosa on 2009-12-13
Hello!

On my **Xubuntu v9.10** system, remastersys v2.0.15.1 (the latest i guess) generates only a LiveCD without any installation options (no icon, sudo ubiquity gives the info, that it crashed).

ISO-Linux starts as usual with the menu. Using the option "install" leads to the same result as using the option "livecd": the livecd system boots but there are no icons to start the installation.

I posted in the remastersys forum and got the answer,
*"Something must be missing from Xubuntu then.  Check and see if they created their own installer in Synaptic and if they did, just install it and try again."*

Do you have ideas what could be missing?
My thanks in advance,
Michael

---

### Post by CongoJim on 2009-12-26
Check to see if you have ubiquity 2.0.9 installed. If you do go to synaptic and click on ubiquity then click on "packages" in the menu bar. There is an option to force version. choose the 2.0.6 version and do the same for other packages that synaptic might demand modification. I added the GTK installer as well.

Worked for me.

---

### Post by babarosa on 2010-01-06
Hi,

I have found the solution.

"Something must be missing from Xubuntu then. Check and see if they created their own installer in Synaptic and if they did, just install it and try again."

Correct, on a vanilla xubuntu system the "GTK+ frontend for Ubiquity live installer" is missing, so use synaptic to install the "ubiquity-frontend-gtk".

Then a remastersysed xubuntu dvd can be used with the "install" option as usual, not only as a live dvd.

---

