---
title: "Apache/Webmin Issues"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by SawnDiddle on 2006-10-04
I have been following this walkthrough on setting up an Ubuntu-server. I have the newest Ubuntu-server. [http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06) and everything was going good until I had to change my listening port from 80 to 8080.

Well, after I turned off Apache2, I could not get it back on.

When I try to load apache, I get the following error.

Failed to start apache:

*Starting apache 2.0 web server...
Syntax error on line 392 of /etc/apache2/apache2.conf:
Port was replaced with Listen in Apache 2.0
...fail!

Anyways, If you take a look at the walkthrough, that is EXACTLY what I have done so far. Nothing extra or more.

If anyone could help me that would be awesome.

P.S. I have also tried returning the port settings to 80 but I still have the same error.

---

### Post by kidders on 2006-10-04
Hi there,

**Syntax error on line 392 of /etc/apache2/apache2.conf: Port was replaced with Listen in Apache 2.0** makes it look as though you're using an obsolete keyword in your apache configuration. Try using the "Listen" directive instead of the "Port" directive, as the message suggests.

---

### Post by SawnDiddle on 2006-10-04
I tried that, but Port was put right back into the apache2.conf file and I still get the same errors.

---

### Post by kidders on 2006-10-05
You mean something modifies your apache configuration behind your back without asking?!

---

### Post by SawnDiddle on 2006-10-05
well, it made the changes when I modified the network settings in webmin. I tried starting Apache2 before making then network modifications and after, but still nothing.

I have no idea why I am getting the error and the error is still persisting.

And even when I try to change Port to Listen and go straight to starting Apache2, I still get the same exact error.

EDIT: Sorry, I went in through Webmin and made changes there and for somereason, Port wasn't put back this time, so it worked. I don't know why or how, but it works and I am happy, thank for the help.

---

### Post by Ning Wan on 2006-10-16
I am encounting the exactly same issue. If there is a fix, please let me know.
I would like to know if somewhere I can find the instruction how to set up apache 2 as a proxy server for zope or plone?
Ning

---

### Post by kidders on 2006-10-18
Hi there,

I imagine the best solution is not to use Webmin to modify your network settings. Are you using the latest version btw?

> I would like to know if somewhere I can find the instruction how to set up apache 2 as a proxy serverApache is a web server, not a proxy. You probably want squid.

---

