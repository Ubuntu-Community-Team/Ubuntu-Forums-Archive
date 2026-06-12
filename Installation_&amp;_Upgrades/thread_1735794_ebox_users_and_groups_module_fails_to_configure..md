---
title: "ebox users and groups module fails to configure."
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by Avanesov on 2011-04-21
I have installed ebox-samba on a fresh install of ubuntu server 10.04 x64.

Made the base install, upgraded to most current packages, installed ebox-samba and dependancies...everything seems to go just fine.


When I log into ebox and select the users and groups module it begins its configuration and then errors out with this message:

```

A really nasty bug has occurred
Exception
Failed to enable: root command ldapadd -H 'ldapi://' -Y EXTERNAL -c -f /var/lib/ebox/tmp/slapd-master.ldif failed. Error output: SASL/EXTERNAL authentication started SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth SASL SSF: 0 ldap_modify: Inappropriate matching (18) additional info: modify/add: olcTLSCACertificateFile: no equality matching rule ldap_modify: Type or value exists (20) additional info: modify/add: olcAccess: value #0 already exists ldap_add: Naming violation (64) ldap_add: Other (e.g., implementation specific) error (80) additional info: olcAttributeTypes: Duplicate attributeType: "0.9.2342.19200300.100.1.2" ldap_add: Other (e.g., implementation specific) error (80) additional info: olcAttributeTypes: Duplicate attributeType: "1.3.6.1.1.1.1.2" ldap_add: Other (e.g., implementation specific) error (80) additional info: olcAttributeTypes: Duplicate attributeType: "2.16.840.1.113730.3.1.1" ldap_modify: Type or value exists (20) additional info: modify/add: olcAccess: value #0 already exists Command output: modifying entry "cn=config" modifying entry "olcDatabase={-1}frontend,cn=config" adding new entry "cn=module{0},cn=config" adding new entry "cn=cosine,cn=schema,cn=config" adding new entry "cn=nis,cn=schema,cn=config" adding new entry "cn=inetorgperson,cn=schema,cn=config" adding new entry "olcDatabase={1}hdb,cn=config" adding new entry "olcOverlay=syncprov,olcDatabase={1}hdb,cn=config" modifying entry "olcDatabase={0}config,cn=config" . Exit value: 20
Trace
Failed to enable: root command ldapadd -H 'ldapi://' -Y EXTERNAL -c -f /var/lib/ebox/tmp/slapd-master.ldif failed.
Error output: SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
ldap_modify: Inappropriate matching (18)
additional info: modify/add: olcTLSCACertificateFile: no equality matching rule
ldap_modify: Type or value exists (20)
additional info: modify/add: olcAccess: value #0 already exists
ldap_add: Naming violation (64)
ldap_add: Other (e.g., implementation specific) error (80)
additional info: olcAttributeTypes: Duplicate attributeType: "0.9.2342.19200300.100.1.2"
ldap_add: Other (e.g., implementation specific) error (80)
additional info: olcAttributeTypes: Duplicate attributeType: "1.3.6.1.1.1.1.2"
ldap_add: Other (e.g., implementation specific) error (80)
additional info: olcAttributeTypes: Duplicate attributeType: "2.16.840.1.113730.3.1.1"
ldap_modify: Type or value exists (20)
additional info: modify/add: olcAccess: value #0 already exists

Command output: modifying entry "cn=config"

modifying entry "olcDatabase={-1}frontend,cn=config"

adding new entry "cn=module{0},cn=config"

adding new entry "cn=cosine,cn=schema,cn=config"

adding new entry "cn=nis,cn=schema,cn=config"

adding new entry "cn=inetorgperson,cn=schema,cn=config"

adding new entry "olcDatabase={1}hdb,cn=config"

adding new entry "olcOverlay=syncprov,olcDatabase={1}hdb,cn=config"

modifying entry "olcDatabase={0}config,cn=config"

.
Exit value: 20 at /usr/share/perl5/EBox/CGI/ServiceModule/ConfigureModuleController.pm line 74
EBox::CGI::ServiceModule::ConfigureModuleController::_process('EBox::CGI::ServiceModule::ConfigureModuleController=HASH(0x7f...') called at /usr/share/perl5/EBox/CGI/Base.pm line 262
EBox::CGI::Base::run('EBox::CGI::ServiceModule::ConfigureModuleController=HASH(0x7f...') called at /usr/share/perl5/EBox/CGI/Run.pm line 120
EBox::CGI::Run::run('EBox::CGI::Run', 'ServiceModule/ConfigureModuleController', 'EBox') called at /usr/share/ebox/cgi/ebox.cgi line 19
ModPerl::ROOT::ModPerl::Registry::usr_share_ebox_cgi_ebox_2ecgi::handler('Apache2::RequestRec=SCALAR(0x7f40b3602f58)') called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 204
eval {...} called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 204
ModPerl::RegistryCooker::run('ModPerl::Registry=HASH(0x7f40b3420900)') called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 170
ModPerl::RegistryCooker::default_handler('ModPerl::Registry=HASH(0x7f40b3420900)') called at /usr/lib/perl5/ModPerl/Registry.pm line 31
ModPerl::Registry::handler('ModPerl::Registry', 'Apache2::RequestRec=SCALAR(0x7f40b3602f58)') called at -e line 0
eval {...} called at -e line 0

```

Does anyone know what that means and/or what I need to do to fix it?

---

