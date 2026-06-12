---
title: "adding Ubuntu server as a file server in Windows network"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by it_suppport on 2008-11-03
Hi All,

We are trying to install & connect Ubuntu server as a member server in our windows 2003 Std network. For this we are using
the latest Ubuntu server 8.04 LTS Hardy.
Our windows Network is made up of win2003 ADS server(adserver) with another as a seperate GC server (gcserver).
We've installed krb5, winbind, Samba, samba-swat in our Ubuntu server.

Whenever I'm trying to connect the ubuntu server in ads, using command ```
net ads join -U <domain_admin_username>%<password>
``` it gives us the error message that the "Host is not configured as a member server".
Please let me know, how can I add the host as a member server to windows AD network.

P.S.: I've also gone thru the ActiveDirectroyWinbindHowto, but it is not helping me much as it has not described the kerberos configuration properly ( this is my personal feeling) or its not working for me.

---

### Post by it_suppport on 2008-11-05
wonders, if no one has done this?

---

### Post by EliteTech on 2008-11-05
I am running into the same issue here. if anyone can help it would be greatly appriciated.

---

### Post by Coreigh on 2008-11-05
Do you have Samba, winbind and kerberos installed and configured with the domain settings?

I will look for the link to the how-to, I have done this many times.

EDIT - Link added:
[Here is the link ...]("http://www.onnoot.com/wiki/how_to_join_ubuntu_samba_to_a_windows_2003_active_directory_domain")

---

