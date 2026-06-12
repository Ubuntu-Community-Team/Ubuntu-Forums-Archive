---
title: "Problem with graphviz / DotEdit - libfontconf1"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by DonKyot on 2006-11-01
Trying to install DotEdit / graphviz

I get the installation error:
E: graphviz-cairo: subprocess post-removal script returned error exit status 127

Trying to load teh package directly from
graphviz_2.8-2.3_i386.deb from 
[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgraphviz%2Fgraphviz_2.8-2.3_i386.deb&md5sum=d27067e1c943689028fdf7fd90c5a981&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgraphviz%2Fgraphviz_2.8-2.3_i386.deb&md5sum=d27067e1c943689028fdf7fd90c5a981&arch=i386&type=main)

Gives dependency not satisfiable: libfontconf1 

Platform: Full installation of Edgy, 2.6.17-10

anyone any ideas? Should the be a bug report.

---

### Post by DonKyot on 2006-11-01
oh! Just installed graphviz & re-installed graphviz-cairo and all is OK.

Somehow, the dependencies are broken in cairo.

---

