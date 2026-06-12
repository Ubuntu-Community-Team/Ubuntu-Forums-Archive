---
title: "tex messed up, Ubuntu 16.04"
date: 2016-10-27
forum: Installation &amp; Upgrades
---

### Post by VanillaMozilla on 2016-10-27
Upgraded from 14.04 to 16.04.  Got a warning that tex could not be configured, and another that upgrade was incomplete and system was unstable.  And that is correct.  I can't install Bombono, for example, and get error messages about tex configuration.  I don't think the upgrade finished and cleaned up the files either.

Here are some diagnostics.  How do I fix this?

>>>>
sudo dpkg --configure -a

```
Setting up tex-common (6.04) ...
Ignoring /etc/texmf/texmf.d/05TeXMF.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/15Plain.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/45TeXinputs.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/55Fonts.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/65BibTeX.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/75DviPS.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/80DVIPDFMx.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/85Misc.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/90TeXDoc.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/95NonPath.cnf during generation of texmf.cnf, please remove manually!


Warning: Old configuration style found in /etc/texmf/updmap.d
Warning: For now these files have been included, 
Warning: but expect inconsistencies.
Warning: These packages should be rebuild with tex-common.
Warning: Please see /usr/share/doc/tex-common/NEWS.Debian.gz
Warning: found file: /etc/texmf/updmap.d/00updmap.cfg
Warning: found file: /etc/texmf/updmap.d/10lmodern.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-base.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-latex-base.cfg

Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... 
updmap-sys failed. Output has been stored in
/tmp/updmap.9guU9s2v
Please include this file if you report a bug.

Sometimes, not accepting conffile updates in /etc/texmf/updmap.d
causes updmap-sys to fail.  Please check for files with extension
.dpkg-dist or .ucf-dist in this directory

dpkg: error processing package tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-luatex:
 texlive-luatex depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-luatex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base-doc:
 texlive-latex-base-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-latex-base-doc (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tex-common
 texlive-luatex
 texlive-latex-base
 texlive-latex-base-doc
```

---

### Post by VanillaMozilla on 2016-10-28
Repair attempts failed.  Solved by removing tex-common completely with Synaptic and reinstalling one program.  Synaptic showed only two programs that depended on tex-common:  one that didn't work after the upgrade, and one that is no longer needed.  So I had nothing to lose.

The remaining problems appear to be minor, but upgrading is getting scary.  Of four computers I upgraded to 16.04, every one required some repairs.  Two were left without a functioning desktop, and one of those is still inoperable.  On the bright side, some programs are now working that have not worked for a long time.  Now if we can just get Gnome and Ubuntu to just fix bugs and not write new ones....

---

