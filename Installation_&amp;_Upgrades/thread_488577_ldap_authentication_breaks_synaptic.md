---
title: "ldap authentication breaks synaptic"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by whitmad on 2007-06-30
I have an Ubuntu feisty workstation configured for openldap authentication, but Synaptic and aptitude no longer work, whether run from a locally authenticated or ldap authenticated user. If I disable ldap authentication by removing the ldap entries from nsswitch.conf, then I can run synaptic or aptitude as a locally authenticated user:

#passwd:         ldap files
#group:          ldap files
#shadow:         ldap files
passwd:         files
group:          files
shadow:         files

With LDAP enabled the error I get from synaptic is: E: ERROR: could not create configuration directory /home/%U/.synaptic - mkdir (2 No such file or directory)

With aptitude, it is "E: /home/%U/.aptitude - mkdir (2 No such file or directory)"

I suspect its something to do with the ldap configuration more than synaptic or aptitude themselves, but not sure. Anyone have any ideas?

---

