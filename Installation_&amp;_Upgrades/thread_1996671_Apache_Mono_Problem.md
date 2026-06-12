---
title: "Apache Mono Problem"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by Tres_Iqus on 2012-06-04
OS: Ubuntu Server 12.04LTS

Apache2 mod mono

My config ASP-directorys with mono-server4 in /etc/mono-server4/mono-server4-hosts.conf

my web pages is not running and asp-samples running very very slow

please help

---

### Post by directhex on 2012-06-04
You've:

[list]
[*]disabled mod_mono_auto
[*]enabled mod_mono
[*]used mono-server4-admin to set up your webapp
[*]restarted apache
[/list]

in that order?

---

### Post by Tres_Iqus on 2012-06-05
reconfigure the server according to your instructions and now throws me this error the application

Server Error in '/sample' Application

The resource cannot be found.

Description: HTTP 404. The resource you are looking for (or one of its dependencies) could have been removed, had its name changed, or is temporarily unavailable. Please review the following URL and make sure that it is spelled correctly.

Requested URL: /sample/

---

