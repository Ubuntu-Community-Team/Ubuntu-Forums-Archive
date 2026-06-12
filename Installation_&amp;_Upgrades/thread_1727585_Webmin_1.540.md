---
title: "Webmin 1.540"
date: 2011-04-12
forum: Installation &amp; Upgrades
---

### Post by andrewqsmith on 2011-04-12
I have Ubuntu Server 10.10 installed and I just updated webmin to latest version. 1.530 worked fine but now when I log into my webmin it gives me the following error:
"Undefined subroutine &WebminCore::theme_prehead called at /usr/share/webmin/web-lib-funcs.pl line 8588."

Please help! This is a headless server and webmin makes life so much easier (though putty is a vital tool as well) thanks for any help you can provide.

---

### Post by z33k3r on 2011-04-13
Having basically the same problem. Upgraded from Webmin 1.53 to 1.540 and it resulted in errors. Updated/upgraded aptitude recommended packages, reboot, now Webmin doesn't start.

---

### Post by SwellJoe on 2011-04-14
andrewqsmith: Restart Webmin. This indicates the current miniserv.pl process is still looking for the old libs. It's supposed to restart during upgrade, but if any errors occurred, that may not have happened. "/etc/init.d/webmin restart"

z33k3r: Your problem is not the same. What error(s) do you get when you try to start Webmin? If there's nothing on the command line, look in the /var/webmin/miniserv.error log, as well as /var/webmin/webmin.log.

---

### Post by z33k3r on 2011-04-14
> **SwellJoe said:**
> z33k3r: Your problem is not the same. What error(s) do you get when you try to start Webmin? If there's nothing on the command line, look in the /var/webmin/miniserv.error log, as well as /var/webmin/webmin.log.

The issue: When I'd do package updates from the Webmin interface, it would break some sort of Perl scripts or links. I don't remember which ones as it's already fixed. Reinstalling Webmin and the retrying the updates resulted in the same. Updating through CLI and then reinstalling Webmin fixed the issue resulted in a usable login.

---

