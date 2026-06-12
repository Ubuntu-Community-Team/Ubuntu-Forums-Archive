---
title: "Dapper OpenOffice and signed documents"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by Pepandy on 2006-11-06
HI,
I'm new to Ubuntu, but have a couple of years on Suse, and wanted to move my work to Ubuntu. Hit a problem immediately.

1. Installed 6.06 on a laptop, and AIUI that will be the one with long term support and the one most new users will see. It contains Ubuntu's version of OOo 2.0.2

2. First doc I tried to open crashed OOo, but the doc was digitally signed. Removed the signature, and it opened fine.

3. Looked around for an update to OOo 2.0.4, and found out how to convert rpms to debs and install with help from the OOo site.

4. Removed OOo 2.0.2 completely from laptop, installed 2.0.4 from OOo's site.

5. Docs now open fine. (And BTW the font wizard is there too so I can get reasonable looking docs from other people who stick to Times New Roman and Ariel.)

Question: Can anyone confirm this behaviour? If so, it looks to me like a bug serious enough to warrant a request for a fix in Dapper.

PS. You can find examples of signed docs at [www.pepperdine.eclipse.co.uk/FOSS](www.pepperdine.eclipse.co.uk/FOSS) and look for the odt and odp versions.

---

### Post by nocturn on 2006-11-06
It may be best to open a bugreport on this one...  I know about signed documents though never use them myslelf (I use PGP, which is not in OO).

---

### Post by Pepandy on 2006-11-07
Bug raised, #70711

---

