---
title: "Issues with encfs, pam,  Xauthority  &amp; ICEauthority in 12.04"
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by why on 2012-05-11
finally found a solution for encrypted HOME dir using encfs over NFS and file locking of Xauthority & ICEauthority in Ubuntu 12.04

Xauthority:
place the following line just before "@include common-auth" in  /etc/pam.d/kdm, /etc/pam.d/gdm, /etc/pam.d/lighdm files you might have (note that I only verified this using kdm, but should work for gdm or lightdm), and now allows the .Xauthority file to be in your HOME dir
[INDENT]auth requisite pam_encfs.so[/INDENT]

ICEauthority:
place the following line at the bottom of the /etc/security/pam_env.conf, which regretfully places the .ICEauthority file on /tmp rather than the users HOME dir
[INDENT]ICEAUTHORITY	DEFAULT=/tmp/.ICEauthority-$USER[/INDENT]

---

