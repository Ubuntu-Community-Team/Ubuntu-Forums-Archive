---
title: "OpenLDAP Ubuntu 11.04"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by Mekik on 2011-06-21
Dear friends,

I am having problem with installation of OpenLDAP on ubuntu server 11.04 on x32 & x64 machine. I follow documentation for server 11.04 on openLDAP server. However, i am stuck at the beginning of the instruction
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif

ERROR: ldap_add: Other (e.g., implementation specific) error (80) Duplicate attributeType: "0.9............"

I search everywhere and test a bunch of command , also reinstall ubuntu from scratch but the issue is still the same.

Could anyone guide me on how to move further. As addition, could anyone help me on how to install slapd & ldap-utils package from scratch beside reinstall ubuntu from scratch.

Thank you in advance.
Warmest Regards,

---

### Post by luvshines on 2011-06-21
Which particular attribute type is giving this error ?
Can you post the complete number that is displayed 0.9....

---

### Post by slooksterpsv on 2011-06-22
> **Mekik said:**
> Dear friends,

I am having problem with installation of OpenLDAP on ubuntu server 11.04 on x32 & x64 machine. I follow documentation for server 11.04 on openLDAP server. However, i am stuck at the beginning of the instruction
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif

ERROR: ldap_add: Other (e.g., implementation specific) error (80) Duplicate attributeType: "0.9............"

I search everywhere and test a bunch of command , also reinstall ubuntu from scratch but the issue is still the same.

Could anyone guide me on how to move further. As addition, could anyone help me on how to install slapd & ldap-utils package from scratch beside reinstall ubuntu from scratch.

Thank you in advance.
Warmest Regards,

Funny you bring this up, I'll make a guide on how to do this as I'm going to write down step by step everything I do and try to replicate it. Cause always when I setup LDAP I miss something. To reinstall slapd and what not you can just do:
sudo apt-get purge ldap-utils

That should purge all the configuration files, should key word. Again I'm working on this tonight to create an LDAP server and client then I'll post back how I do it.

---

### Post by Mekik on 2011-06-22
Dear slooksterpsv,luvshines,

Good day.

Exact error code for each command are as follows:-
*sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif*
additional info: olcAttributeType: Duplicate attributeType: "0.9.2342.19200300.100.1.2"

*sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif*
additional info: olcAttributeType: Duplicate attributeType: "1.3.6.1.1.1.1.2"

*sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif*
additional info: olcAttributeType: Duplicate attributeType: "2.16.840.1.113730.3.1.1"

Your cooperation and support are highly appreciated.

Warmest Regards,

---

### Post by Mekik on 2011-06-25
Dear Friends,

Everything are working fine now... Just ignored the error of duplicateAttributeType because all schema are included by default.

please check slapd.conf. Hope Ubuntu team would allow public user to make amendment to the community documentation where needed.

Thank you. I love Ubuntu.

Regards,

---

### Post by jwxie on 2013-01-08
> **Mekik said:**
> Dear Friends,

Everything are working fine now... Just ignored the error of duplicateAttributeType because all schema are included by default.

please check slapd.conf. Hope Ubuntu team would allow public user to make amendment to the community documentation where needed.

Thank you. I love Ubuntu.

Regards,

I can't find slooksterpsv's proposed guide lol. I think he never had the time to make it.

Any case, it is now included in the documentation.
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)
> As of Ubuntu Natty (and possibly prior to it), the 3 basic schemas, (inetorgperson, cosine, and nis) do not have to be loaded manually, contrary to the Ubuntu Server Guide's instructions. These schemas are loaded as part of the installation process.

---

