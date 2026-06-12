---
title: "OpenOffice bug hits multiple operating systems"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by The Fire Fly on 2008-03-21
Security experts have discovered vulnerabilities in OpenOffice.org that could allow attackers to remotely execute code on Linux, Windows or Apple Mac-based computers. 

OpenOffice version 2.0.4 and earlier versions are vulnerable to maliciously crafted TIFF files, which can be delivered in an e-mail attachment, published on a Web site or shared using peer-to-peer software. The next version of OpenOffice (version 2.3) arrived on September 17 and is not affected by the flaw. 

The vulnerability was discovered by researchers at iDefense, who claim that the OpenOffice TIFF parsing code is flawed. 

"When parsing the TIFF directory entries for certain tags, the parser uses untrusted values from the file to calculate the amount of memory to allocate. By providing specially crafted values, an integer overflow occurs in this calculation. This results in the allocation of a buffer of insufficient size, which in turn leads to a heap overflow," the iDefense team reported last Friday. 

TrustDefender co-founder Andreas Baumhof said: "This vulnerability allows someone to execute malicious code on your computer. It's an OpenOffice bug so it doesn't matter what type of operating system you run; it allows you to run malicious software with the same rights as the user who runs OpenOffice."

---

