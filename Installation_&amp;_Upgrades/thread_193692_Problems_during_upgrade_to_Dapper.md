---
title: "Problems during upgrade to Dapper"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by markprice81 on 2006-06-10
When I tried to upgrade to Dapper, the installation process froze and I had to reboot. Since then I have been attempting to upgrade all the packages from the terminal but I have become stuck and am unable to solve the following.

When I run dpkg --configure -a I get

dpkg: dependency problems prevent configuration of jmpost:
 jmpost depends on tetex-bin (>= 1.0.7+20011202-5.1); however:
  Package tetex-bin is not installed.
dpkg: error processing jmpost (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tfm-arphic-bsmi00lp:
 tfm-arphic-bsmi00lp depends on tetex-bin; however:
  Package tetex-bin is not installed.
dpkg: error processing tfm-arphic-bsmi00lp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tfm-arphic-gkai00mp:
 tfm-arphic-gkai00mp depends on tetex-bin; however:
  Package tetex-bin is not installed.
dpkg: error processing tfm-arphic-gkai00mp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hlatex:
 hlatex depends on tetex-bin (>= 3); however:
  Package tetex-bin is not installed.
 hlatex depends on tetex-base (>= 3); however:
  Package tetex-base is not installed.
dpkg: error processing hlatex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of musixtex:
 musixtex depends on tetex-base (>= 1.0-1); however:
  Package tetex-base is not installed.
 musixtex depends on tetex-bin (>= 1.0.5-1); however:
  Package tetex-bin is not installed.
dpkg: error processing musixtex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ethiop:
 ethiop depends on tetex-base; however:
  Package tetex-base is not installed.
 ethiop depends on tetex-bin; however:
  Package tetex-bin is not installed.
dpkg: error processing ethiop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jbibtex-base:
 jbibtex-base depends on tetex-base; however:
  Package tetex-base is not installed.
 jbibtex-base depends on tetex-bin; however:
  Package tetex-bin is not installed.
dpkg: error processing jbibtex-base (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 jmpost
 tfm-arphic-bsmi00lp
 tfm-arphic-gkai00mp
 hlatex
 musixtex
 ethiop
 jbibtex-base

If I run dselect and attempt to remove the packages I get

running dpkg --pending --remove ...
(Reading database ... 303638 files and directories currently installed.)
Removing opustex ...
/var/lib/dpkg/info/opustex.postrm: line 14: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing opustex (--remove):
 subprocess post-removal script returned error exit status 1
Removing tfm-arphic-bkai00mp ...
/var/lib/dpkg/info/tfm-arphic-bkai00mp.postrm: line 19: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing tfm-arphic-bkai00mp (--remove):
 subprocess post-removal script returned error exit status 1
Removing musixtex-slurps ...
/var/lib/dpkg/info/musixtex-slurps.postrm: line 23: /usr/bin/mktexlsr: No such file or directory
dpkg: error processing musixtex-slurps (--remove):
 subprocess post-removal script returned error exit status 1
Removing latex209-bin ...
/var/lib/dpkg/info/latex209-bin.prerm: line 22: mktexlsr: command not found
dpkg: error processing latex209-bin (--remove):
 subprocess pre-removal script returned error exit status 127
Removing ptex-base ...
/var/lib/dpkg/info/ptex-base.postrm: line 22: mktexlsr: command not found
dpkg: error processing ptex-base (--remove):
 subprocess post-removal script returned error exit status 127
Removing tfm-arphic-gbsn00lp ...
/var/lib/dpkg/info/tfm-arphic-gbsn00lp.postrm: line 19: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing tfm-arphic-gbsn00lp (--remove):
 subprocess post-removal script returned error exit status 1
Removing latex-ucs ...
/var/lib/dpkg/info/latex-ucs.postrm: line 12: mktexlsr: command not found
dpkg: error processing latex-ucs (--remove):
 subprocess post-removal script returned error exit status 127
Removing hbf-jfs56 ...
/var/lib/dpkg/info/hbf-jfs56.prerm: line 19: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing hbf-jfs56 (--remove):
 subprocess pre-removal script returned error exit status 1
Removing latex-ucs-uninames ...
/var/lib/dpkg/info/latex-ucs-uninames.postrm: line 7: mktexlsr: command not found
dpkg: error processing latex-ucs-uninames (--remove):
 subprocess post-removal script returned error exit status 127
Removing dvipsk-ja ...
/var/lib/dpkg/info/dvipsk-ja.prerm: line 24: mktexlsr: command not found
dpkg: error processing dvipsk-ja (--remove):
 subprocess pre-removal script returned error exit status 127
Removing jlatex209-bin ...
/var/lib/dpkg/info/jlatex209-bin.prerm: line 22: mktexlsr: command not found
dpkg: error processing jlatex209-bin (--remove):
 subprocess pre-removal script returned error exit status 127
Removing latex-ucs-contrib ...
/var/lib/dpkg/info/latex-ucs-contrib.postrm: line 7: mktexlsr: command not founddpkg: error processing latex-ucs-contrib (--remove):
 subprocess post-removal script returned error exit status 127
Removing multex-bin ...
/var/lib/dpkg/info/multex-bin.prerm: line 24: mktexlsr: command not found
dpkg: error processing multex-bin (--remove):
 subprocess pre-removal script returned error exit status 127
Removing jbibtex-bin ...
mv: cannot stat `/etc/texmf/texmf.d/60jbibtex.cnf': No such file or directory
dpkg: error processing jbibtex-bin (--remove):
 subprocess post-removal script returned error exit status 1
dpkg: dependency problems prevent removal of multex-base:
 multex-bin depends on multex-base (>= 0.8).
dpkg: error processing multex-base (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of jtex-base:
 multex-bin depends on jtex-base (>= 1.9.1); however:
  Package jtex-base is to be removed.
dpkg: error processing jtex-base (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of latex209-base:
 jlatex209-bin depends on latex209-base; however:
  Package latex209-base is to be removed.
 latex209-bin depends on latex209-base; however:
  Package latex209-base is to be removed.
dpkg: error processing latex209-base (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of jlatex209-base:
 jlatex209-bin depends on jlatex209-base.
dpkg: error processing jlatex209-base (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of jtex-bin:
 jlatex209-bin depends on jtex-bin (>= 1.9.1-3).
dpkg: error processing jtex-bin (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 opustex
 tfm-arphic-bkai00mp
 musixtex-slurps
 latex209-bin
 ptex-base
 tfm-arphic-gbsn00lp
 latex-ucs
 hbf-jfs56
 latex-ucs-uninames
 dvipsk-ja
 jlatex209-bin
 latex-ucs-contrib
 multex-bin
 jbibtex-bin
 multex-base
 jtex-base
 latex209-base
 jlatex209-base
 jtex-bin

dpkg --remove returned error exit status 1.

If I run apt-get remove -f I get 

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  tetex-base tetex-bin tex-common
Suggested packages:
  tetex-extra gs-gpl texi2html dvipng rubber sam2p
Recommended packages:
  tetex-doc perl-tk
The following packages will be REMOVED:
  jbibtex-bin latex-ucs-contrib latex-ucs-uninames
The following NEW packages will be installed:
  tetex-base tetex-bin tex-common
0 upgraded, 3 newly installed, 3 to remove and 982 not upgraded.
20 not fully installed or removed.
Need to get 0B/29.2MB of archives.
After unpacking 85.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 303638 files and directories currently installed.)
Removing jbibtex-bin ...
mv: cannot stat `/etc/texmf/texmf.d/60jbibtex.cnf': No such file or directory
dpkg: error processing jbibtex-bin (--remove):
 subprocess post-removal script returned error exit status 1
Removing latex-ucs-contrib ...
/var/lib/dpkg/info/latex-ucs-contrib.postrm: line 7: mktexlsr: command not founddpkg: error processing latex-ucs-contrib (--remove):
 subprocess post-removal script returned error exit status 127
Removing latex-ucs-uninames ...
/var/lib/dpkg/info/latex-ucs-uninames.postrm: line 7: mktexlsr: command not found
dpkg: error processing latex-ucs-uninames (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 jbibtex-bin
 latex-ucs-contrib
 latex-ucs-uninames
E: Sub-process /usr/bin/dpkg returned an error code (1)

If I run apt-get install -f I get 

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  tetex-base tetex-bin tex-common
Suggested packages:
  tetex-extra gs-gpl texi2html dvipng rubber sam2p
Recommended packages:
  tetex-doc perl-tk
The following packages will be REMOVED:
  jbibtex-bin latex-ucs-contrib latex-ucs-uninames
The following NEW packages will be installed:
  tetex-base tetex-bin tex-common
0 upgraded, 3 newly installed, 3 to remove and 982 not upgraded.
20 not fully installed or removed.
Need to get 0B/29.2MB of archives.
After unpacking 85.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 303638 files and directories currently installed.)
Removing jbibtex-bin ...
mv: cannot stat `/etc/texmf/texmf.d/60jbibtex.cnf': No such file or directory
dpkg: error processing jbibtex-bin (--remove):
 subprocess post-removal script returned error exit status 1
Removing latex-ucs-contrib ...
/var/lib/dpkg/info/latex-ucs-contrib.postrm: line 7: mktexlsr: command not founddpkg: error processing latex-ucs-contrib (--remove):
 subprocess post-removal script returned error exit status 127
Removing latex-ucs-uninames ...
/var/lib/dpkg/info/latex-ucs-uninames.postrm: line 7: mktexlsr: command not found
dpkg: error processing latex-ucs-uninames (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 jbibtex-bin
 latex-ucs-contrib
 latex-ucs-uninames
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help on how to proceed would be greatly appreciated it.

Mark

---

### Post by nebula on 2006-06-10
I have kind of the same problem, but my network support is also wrecked, i posted my problem here (last post): [http://www.ubuntuforums.org/showthread.php?t=148775](http://www.ubuntuforums.org/showthread.php?t=148775).

Any help would be greatly appreciated!

---

### Post by nebula on 2006-06-12
Ah well I found the answer to 90% of the problems!
If you follow this: [http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)
You should get a bit further. Don't be afraid to throw out some of the non functioning packages if you must.
Still, one problem remains... 
If I now try to sudo (which I could before) I get the following:

sudo: must be setuid root.
[edit] fixed with chmod 4111 /usr/bin/sudo[/edit]

I also hold the super-user password, so if I try to su from my regular user name and type the correct password it says:

getgid: Operation not permitted.

As a last reort I logged out, and tried to login as root but...

Ubuntu 6.06 LTS lion-0 tty2

lion-0 login: root
Login incorrect

What?! (I thought) I didn't even enter a password?!
If I boot in recovery mode however then my root login does work when it promts for it. So there is a small opening for me to actually do something on my system.

Could this be related with the fact that I (when trying to recover my system) issued the command
/# chmod 777 / -R
And can this be undone without editing all of my files back to the normal access parameters?

Thanks!

Nebula

---

