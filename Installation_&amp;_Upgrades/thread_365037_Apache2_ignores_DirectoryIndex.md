---
title: "Apache2 ignores DirectoryIndex"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by BillRebey on 2007-02-19
Apache2 appears to ignore DirectoryIndex.  It will only automatically load "index.htm" files.  It won't automatically load "index.html" files,  or anything else that I put in the DirectoryIndex list.  

I have several virtual domains, and I've tried placing the DirectoryIndex directive in apache2.conf, as well as within the individual domain configuration files in /etc/apache2/sites-available (which are symlinked from ..../sites-enabled).  Nothing changes.

If I take it out altogether, if I put only one item in the list - nothing matters.  Apache loads index.htm and nothing else.

Any thoughts?

---

### Post by Koybe on 2007-02-19
What if you verify the syntax? apache2 -t
Don't you have multiple declaration of DirectoryIndex? Maybe one is corrupted : grep -ri DirectoryIndex /etc/apache2
And don't have really much idea but maybe this could open a way.

---

