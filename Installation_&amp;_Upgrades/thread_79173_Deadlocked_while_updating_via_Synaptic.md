---
title: "Deadlocked while updating via Synaptic"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by alexj on 2005-10-19
Hi guys,

[COLOR="Sienna"]Attempted upgrade as recommended, choose different English when asked (UK instead of US). Now it halts every time I try "Apply" or run "apt-get -f install" :[/COLOR]

[INDENT]Preconfiguring packages ...
(Reading database ... 83182 files and directories currently installed.)
Unpacking openoffice.org2-help-en-us (from .../openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb) ...
dpkg: error processing /var/cache/apt/archives/openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice2/help/en/scalc.idx/DOCS.TAB', which is also in package openoffice.org2-calc
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/INDENT]

---

### Post by wgscott on 2005-10-19
Judging by what you said, the problem is probably being caused by this:

Unpacking openoffice.org2-help-en-**us**

So maybe the thing to do is switch back to US English, finish the install, and then return to the Queen's lingo.

---

