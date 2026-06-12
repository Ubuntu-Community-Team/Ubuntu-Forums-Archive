---
title: "command to set autologin in Oneiric"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by CarlFK on 2011-10-15
where does "system settings, user accounts, auto login=yes" get stored?  I want a script to set it.

I have an automated pxe install setup.  for Natty this worked:

cat <<EOT >/etc/gdm/$CONF
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=$NUSER
EOT

---

