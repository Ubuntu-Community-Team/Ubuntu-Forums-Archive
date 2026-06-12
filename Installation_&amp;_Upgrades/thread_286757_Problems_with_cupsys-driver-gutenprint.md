---
title: "Problems with cupsys-driver-gutenprint"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by rtmie on 2006-10-28
Hi ,
I just upgraded to edgy (X86-64) - almost smoothly.

I am having a probmem with the cupsys-driver-gutenprint package.
The package fails in the configure stage of it's install while running 
/usr/sbin/cups-genppdconfig.5.0

>sudo apt-get install cupsys-driver-gutenprint

returns:

Setting up cupsys-driver-gutenprint (5.0.0-2ubuntu2) ...
can't close cups-genppd pipe:  at /usr/sbin/cups-genppdconfig.5.0 line 418.
dpkg: error processing cupsys-driver-gutenprint (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 cupsys-driver-gutenprint
E: Sub-process /usr/bin/dpkg returned an error code (1)

Running usr/sbin/cups-genppdconfig.5.0 manually like:
> usr/sbin/cups-genppdconfig.5.0 -u  
results in:

Writing /usr/share/ppd/gutenprint/5.0/en/stp-bjc-30.5.0.ppd.gz...
cups-genppd.5.0: symbol lookup error: cups-genppd.5.0: undefined symbol: stp_get_maximum_imageable_area
can't close cups-genppd pipe:  at /usr/sbin/cups-genppdconfig.5.0 line 418.



I've tried removing and reinstalling all gutenprint libs etc to no avail, and googling the symbol lookup error didn't show anything useful.

Any help would be gratefully received (my wife needs access to printer this weekend - and I could be in big trouble for :-(

Rob M

---

### Post by rtmie on 2006-11-03
Apparently the  workaround is to try to install cupsys-driver-gutenprint. 
After it fails do:
> sudo mkdir -p /usr/share/cups/model/gutenprint/5.0/en

then 
>sudo apt-get install cupsys-driver-gutenprint

then
>sudo /usr/sbin/cups-genppdconfig-5.0 -u

(Found somewhere in Debian mailing list, can't find the reference right now).

Rob M

---

