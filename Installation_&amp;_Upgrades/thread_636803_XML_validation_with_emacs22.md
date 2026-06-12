---
title: "XML validation with emacs22"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by fnielsen on 2007-12-10
Am I having problem with XML validation in Ubuntu Gutsy: 

1) Validation via emacs21 with a UTF-8 file with nsgmls shows "non SGML character number", though the editor "kate" shows the specific character alright.  

2) I installed the emacs22 package. When I reinstall the psgml it does not compile with emacs22. Synaptic reports:

install/psgml: Ignoring emacs.
install/psgml: Byte-compiling for emacs21... done.
install/psgml: Ignoring emacsen flavor emacs22.

When I C-c C-v emacs22 just suggest the command "Validate command: nsgmls -s woexts.xml"

In Debian there seems to have been a similar problem for the auctex package, see
[http://www.mail-archive.com/debian-bugs-closed%40lists.debian.org/msg137654.html](http://www.mail-archive.com/debian-bugs-closed%40lists.debian.org/msg137654.html)

xmllint works report no errors with this: "xmllint --valid --noout woexts.xml"

/Finn Årup Nielsen

---

### Post by fnielsen on 2008-05-07
In Ubuntu Hardy XML validation now works in emacs22 and emacs21 through nXML.

---

