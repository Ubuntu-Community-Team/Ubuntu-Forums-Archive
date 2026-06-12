---
title: "Package Operation Failed"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by gavdari on 2010-08-09
Recently when I try to install or remove a package from software center I receive an error:
Package Operation Failed
When I click on details the following is shown (It's for removing Winefish)

[INDENT]installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 197789 files and directories currently installed.) 
Removing winefish ... 
Processing triggers for menu ... 
Processing triggers for man-db ... 
Processing triggers for shared-mime-info ... 
Unknown media type in type 'all/all' 
 
Unknown media type in type 'all/allfiles' 
 
Unknown media type in type 'uri/mms' 
 
Unknown media type in type 'uri/mmst' 
 
Unknown media type in type 'uri/mmsu' 
 
Unknown media type in type 'uri/pnm' 
 
Unknown media type in type 'uri/rtspt' 
 
Unknown media type in type 'uri/rtspu' 
 
Unknown media type in type 'fonts/package' 
 
Unknown media type in type 'interface/x-winamp-skin' 
 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for python-support ... 
Setting up tex-common (2.06) ... 
Running mktexlsr. This may take some time... done. 
No packages found matching texlive-base. 
dpkg: error processing tex-common (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of texlive-binaries: 
 texlive-binaries depends on tex-common (>= 2.00); however: 
  Package tex-common is not configured yet. 
dpkg: error processing texlive-binaries (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing: 
 tex-common 
 texlive-binaries 
Setting up tex-common (2.06) ... 
Running mktexlsr. This may take some time... done. 
No packages found matching texlive-base. 
dpkg: error processing tex-common (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of texlive-binaries: 
 texlive-binaries depends on tex-common (>= 2.00); however: 
  Package tex-common is not configured yet. 
dpkg: error processing texlive-binaries (--configure): 
 dependency problems - leaving unconfigured 
[/INDENT]
I guess it's no big deal, since Winefish is removed after all (and all other packages with similar error), but it's kind of annoying. Is there any way to fix it?

---

