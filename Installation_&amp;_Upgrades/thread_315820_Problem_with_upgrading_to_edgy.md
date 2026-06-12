---
title: "Problem with upgrading to edgy"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by macozz on 2006-12-09
Hi al,
I just try the upgrade from dapper and all (or almost) runs OK, but the samba package refuse to upgrade and prevent other upgrades.
I found several tips in the forums, particularly those mentioning the symlinks, but no one worked upt to now.
This is what I get running "sudo apt-get -f install":

Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu4_i386.deb) ...
Unpacking replacement samba ...
/var/lib/dpkg/info/samba.postrm: 24: update-inetd: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 24: update-inetd: not found
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 24: update-inetd: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I nor even can uninstall the package or fix it.
Any clues?

Thank you very much!

Mario

---

### Post by macozz on 2006-12-12
Well, I solved it. I installed the update-inetd package available (apparently) only for Feisty (I have the Feity kernel, 2.6.19-7) and =that let me remove samba en reinstall it.
Cheers.

---

