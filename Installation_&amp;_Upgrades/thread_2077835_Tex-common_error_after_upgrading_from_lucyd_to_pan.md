---
title: "Tex-common error after upgrading from lucyd to pangolin"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by Soonick on 2012-10-29
Hello everybody.
I upgraded from ubuntu lucyd to pangolin and almost everything is gone fine.
The only problem that now i have concerns the tex-common package.
I think it is a bug ([https://bugs.launchpad.net/ubuntu/+source/tex-common/+bug/931274](https://bugs.launchpad.net/ubuntu/+source/tex-common/+bug/931274) ).
Anyway, when I try to do a number of operation, I receive the following error:
```
Configurazione di tex-common (2.10)...
Not replacing deleted config file /etc/texmf/texmf.d/05TeXMF.cnf
Not replacing deleted config file /etc/texmf/texmf.d/15Plain.cnf
Not replacing deleted config file /etc/texmf/texmf.d/45TeXinputs.cnf
Not replacing deleted config file /etc/texmf/texmf.d/55Fonts.cnf
Not replacing deleted config file /etc/texmf/texmf.d/65BibTeX.cnf
Not replacing deleted config file /etc/texmf/texmf.d/75DviPS.cnf
Not replacing deleted config file /etc/texmf/texmf.d/85Misc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/90TeXDoc.cnf
Not replacing deleted config file /etc/texmf/texmf.d/95NonPath.cnf
Not replacing deleted config file /etc/texmf/updmap.d/00updmap.cfg
update-texmf: Basic configuration file /etc/texmf/texmf.d/05TeXMF.cnf missing.
Exiting.
dpkg: error during elaboration of tex-common (--configure):
 the old subprocess script of post-installation returned the error status 1
No apport report written because MaxReports has already been reached
 There are some errors in the elaboration of:
 tex-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
nedu@nedu:~$ 

```Any idea please?

---

### Post by Soonick on 2012-10-31
No one?
this problem is affecting a lot of procedures....

---

### Post by Zilvador on 2012-11-13
Hi Soonick.

I had the same error, but it works now. Have a look at my comment on the original bug report: [URL="https://bugs.launchpad.net/ubuntu/+source/tex-common/+bug/873567"]https://bugs.launchpad.net/ubuntu/+source/tex-common/+bug/873567 .
[/URL] 
Be aware though that it is more of a work-around than a fix and that you should be careful about touching system files. That is why I move them to another directory instead of deleting them. Then you can always move them back.

Best regards, Zilvador.

---

