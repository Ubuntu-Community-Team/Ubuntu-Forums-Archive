---
title: "Problem installing compiz 0.6.2"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by jacques83 on 2008-04-11
Hey folks

Im a newbie to linux, and am using enterprise linux 5 (redhat+gnome)

I did a tar -zxvf on the compiz .tar.gz file, and got the following install file...

compiz uses libstartup-notification which is available at
[ftp://ftp.gnome.org/pub/GNOME/sources/startup-notification/](ftp://ftp.gnome.org/pub/GNOME/sources/startup-notification/)

compiz uses automake, in order to generate the Makefiles for compiz use:

	$ autogen.sh

After that, standard build procedures apply:

	$ make
	# make install
------------------------------------------------------------
I am not sure as to how do I go ahead wid this installation. Can someone please guide me?

I do not see any autogen.sh file in the compiz folder generated.

Thanks

AJ

---

