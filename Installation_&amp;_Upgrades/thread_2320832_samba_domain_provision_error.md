---
title: "samba domain provision error"
date: 2016-04-18
forum: Installation &amp; Upgrades
---

### Post by Abu_Khalid on 2016-04-18
I following tutorial make a active directory and domain control from youtube and stuck here..

# /usr/local/samba/bin/samba-tool domain provision

Realm [JUNIUS7]: junius7.com
 Domain [junius7]: 
 Server Role (dc, member, standalone) [dc]: 
 DNS backend (SAMBA_INTERNAL, BIND9_FLATFILE, BIND9_DLZ, NONE) [SAMBA_INTERNAL]: 
 DNS forwarder IP address (write 'none' to disable forwarding) [202.162.192.10]: 
Administrator password: 
Invalid administrator password.
Administrator password: 
Retype password: 
ERROR(<class 'samba.provision.ProvisioningError'>): Provision failed - ProvisioningError: guess_names: Domain 'JUNIUS7' must not be equal to short host name 'JUNIUS7'!
  File "/usr/local/samba/lib64/python2.7/site-packages/samba/netcmd/domain.py", line 461, in run
    nosync=ldap_backend_nosync, ldap_dryrun_mode=ldap_dryrun_mode)
  File "/usr/local/samba/lib64/python2.7/site-packages/samba/provision/__init__.py", line 2024, in provision
    sitename=sitename, rootdn=rootdn, domain_names_forced=(samdb_fill == FILL_DRS))
  File "/usr/local/samba/lib64/python2.7/site-packages/samba/provision/__init__.py", line 626, in guess_names
    raise ProvisioningError("guess_names: Domain '%s' must not be equal to short host name '%s'!" % (domain, netbiosname))

help me please..

---

