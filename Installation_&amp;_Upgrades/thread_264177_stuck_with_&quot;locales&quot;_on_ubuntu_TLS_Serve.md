---
title: "stuck with &quot;locales&quot; on ubuntu TLS Server"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by Ubimad on 2006-09-24
Hi everyone
have really headache with the "locales" on my Ubuntu TLS Server.
Have it on a Xen domU runing, installed it with "debootstrap"
Like to have de_CH.ISO-8859-1 as my locale.
Tryed many different things but somehow it does not work, the way I like to see it. I do:
[LIST=1]
[*]dpkg-reconfigure localeconf and set everything to "de_CH.ISO-8859-1"
[*]dpkg-reconfigure locales
[*]reboot
[/LIST]
then still in the nano editor the öäü for German is not propperly displayed.
as far as I understand it should be set with "localconf"
has anyone a idea why it still gives me trouble.

thanks
Tobias

/etc/environment looks like this:

GNU  GNU nano 1.3.10                    Datei: /etc/environment

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="de_CH.ISO-8859-1"
LANGUAGE="de_CH:de"

### BEGIN DEBCONF SECTION FOR localeconf
# Do not edit within this region if you want your changes to be preserved
# by debconf.  Instead, make changes before the "### BEGIN DEBCONF SECTION
# FOR localeconf" line, and/or after the "### END DEBCONF SECTION FOR
# localeconf" line.
LANG=de_CH
### END DEBCONF SECTION FOR localeconf

/usr/share/i18n/SUPPORTED
has also everything:

de_AT ISO-8859-1
de_AT@euro ISO-8859-15
de_BE.UTF-8 UTF-8
de_BE ISO-8859-1
de_BE@euro ISO-8859-15
de_CH.UTF-8 UTF-8
de_CH ISO-8859-1
de_DE.UTF-8 UTF-8
de_DE ISO-8859-1
de_DE@euro ISO-8859-15

---

