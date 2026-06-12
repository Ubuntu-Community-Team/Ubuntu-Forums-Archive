---
title: "automating answer to question about conflicting config files (nagios-nrpe-server)"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by bchill on 2010-07-14
Hello,

I did a debconf-get-selections with and without the --installer option and don't see any nagios or nrpe preseed entries.

I don't care which config file the installer uses if any, since I am going overwrite it later anyway - I just want NRPE and other software (dhcp server is another example) with this same problem installed without any questions.

How do suppress this question?

==============================================================
Configuration file `/etc/nagios/nrpe.cfg'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** nrpe.cfg (Y/I/N/O/D/Z) [default=N] ? 
==============================================================


Thanks for any help.

Brian

---

