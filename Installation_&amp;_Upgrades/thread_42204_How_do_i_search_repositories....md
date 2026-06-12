---
title: "How do i search repositories..."
date: 2005-06-16
forum: Installation &amp; Upgrades
---

### Post by vtechstu on 2005-06-16
How do i search the apt-get repos. for certain files?  Thanks.

---

### Post by imightbegiant on 2005-06-16
[QUOTE=vtechstu]How do i search the apt-get repos. for certain files?  Thanks.[/QUOTE]
 The easiest way is through synaptic. System>Administration>Synaptic Package Manger. and use the search function.

or through the command line

$ sudo apt-cache search <package>

check out [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) for more details

---

### Post by vtechstu on 2005-06-16
Thanks.  Works good, but i can't seem to find what i'm looking for.  I need to install  libc6 2.3.2.ds1-20ubuntu13 but can't find the 2.3.2.ds1-20ubuntu13 anywhere.  I have wrong version of libc6 installed.

---

### Post by Xian on 2005-06-16
You can search for packages at the [Ubuntu Packages](http://packages.ubuntu.com/) website.
Here is the [result](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libc6&searchon=names&subword=1&version=hoary&release=all) for your query.

---

### Post by imightbegiant on 2005-06-16
[QUOTE=vtechstu]Thanks.  Works good, but i can't seem to find what i'm looking for.  I need to install  libc6 2.3.2.ds1-20ubuntu13 but can't find the 2.3.2.ds1-20ubuntu13 anywhere.  I have wrong version of libc6 installed.[/QUOTE]
 That version of libc6 is the latest version supported by Hoary and should be showing up. If you haven't enabled the extra repositories yet that would be a good idea. Check out the ubuntuguide for that.  Make sure you reload your package lists in synaptic or run a 

$ sudo apt-get update

and then search for libc6.

---

