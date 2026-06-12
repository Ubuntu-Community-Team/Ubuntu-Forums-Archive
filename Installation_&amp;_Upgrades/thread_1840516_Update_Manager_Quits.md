---
title: "Update Manager Quits"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by kw12589 on 2011-09-07
When I run update manager I get the following failed to download repository warning.

> W:Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release](http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release)  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

This occurs when I select Check and Update Manager starts Updating Cache.

I have deleted the virtual box PP; no help.
I have installed virtual box from Synaptic Package Manager, reported success; no help

Thanks,
Keith

---

### Post by raja.genupula on 2011-09-07
open your update manager -->settings-->other software--> uncheck the Source of error source and then update again 

let us know what you got

---

### Post by kw12589 on 2011-09-08
Yes, I just founf that a minute ago!
I unchecked virtualbox references and all works fine now.

Thanks for the help!

Keith

PS: How can I mark this as solved?

---

