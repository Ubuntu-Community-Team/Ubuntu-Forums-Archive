---
title: "apache2 init.d file points to httpd.conf and not apache2.conf"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by bigal99 on 2007-04-29
I have installed feisty 7.04 on a new Intel system.

I am trying to learn what is new with apache 2.2.

I notice that now there is an /etc/apache2/apache2.conf file and that it has an 'include' for httpd.conf within.

However, I see that in /etc/init.d/apache2 script, the startup only looks for an httpd.conf and not an apache2.conf

"...
        start)
                [ -f /etc/apache2/httpd.conf ] || touch /etc/apache2/httpd.conf

..."

Can anyone help clarify this?

---

### Post by bigal99 on 2007-04-30
Doing a;
# strings /usr/sbin/apache2 | grep '/' | more

yields;
 -D AP_TYPES_CONFIG_FILE="/etc/apache2/mime.types"
 -D SERVER_CONFIG_FILE="/etc/apache2/apache2.conf"

among many other lines (I love the 'strings' command <g>).

This indicates that the default configuration file '/etc/apache2/apache2.conf' seems to be built right in to the executable.

---

