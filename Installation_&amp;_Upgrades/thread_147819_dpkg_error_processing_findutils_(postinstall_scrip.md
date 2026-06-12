---
title: "dpkg: error processing findutils (postinstall script problem)"
date: 2006-03-20
forum: Installation &amp; Upgrades
---

### Post by usrloco on 2006-03-20
I'm having a problem getting the latest updates to Ubuntu Dapper. I'm getting the following error from `apt-get upgrade' (also from synaptic):

Preconfiguring packages ...
Setting up findutils (4.2.27-1ubuntu1) ...
install-info: No such file or directory for Basics  <------------
dpkg: error processing findutils (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 findutils
E: Sub-process /usr/bin/dpkg returned an error code (1)

The file /var/lib/dpkg/info/findutils.postinst includes the following fragment, which seems to be where things are going wrong:

# Automatically added by dh_installinfo
if [ "$1" = "configure" ]; then
	install-info --quiet --section "\QBasics\E" "Basics" /usr/share/info/find.info
fi
# End automatically added section

I'm not sure what exactly this all means. Doing a zgrep for Basic in /usr/share/info/find.info.gz does turn up something that looks promising:

INFO-DIR-SECTION Basics

But that's about as far as I can get. Anyone know how to fix this?

---

### Post by usrloco on 2006-03-20
Problem fixed:

The problem was that there was another version of install-info in /usr/local/bin, which is higher up in my PATH. I had installed something (TeX Live) by hand from disk yesterday, and it must have come with its own version of install-info.

---

