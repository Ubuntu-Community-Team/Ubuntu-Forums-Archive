---
title: "perl module???"
date: 2004-12-19
forum: Installation &amp; Upgrades
---

### Post by molvistan on 2004-12-19
i was trying to install Coaster but half way through the install i got the following error message:

checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool


how can i get round this.

thanks

---

### Post by nemin on 2004-12-19
[QUOTE=molvistan]
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool[/QUOTE]
This should be enough:
perl -MCPAN -e "install XML::Parser"

You have to enter some information the first time.

---

