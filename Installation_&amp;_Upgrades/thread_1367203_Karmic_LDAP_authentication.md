---
title: "Karmic LDAP authentication"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by bobwdn on 2009-12-29
I have a Karmic server with LDAP on it. I am trying to authenticate a (second computer) Karmic desktop to it. I am quite new at LDAP, so forgive my lack of proper knowledge.

On my desktop I have installed LDAP Administration Tool (LAM) and it can "see" my LDAP server at the proper ip address.

I find that most of the documentation I have found is not current enough to apply to Karmic. (Something about "As of pam 1.0.1-6" appears in all the config file notes.) Apparently Karmic authentication is updated and different from all past Ubuntu versions.

My auth.log file has many entries of "nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server" and "nss_ldap: failed to bind to LDAP server ldapi:///192.168.0.153:389: Can't contact LDAP server".

Where is Karmic documentation regarding LDAP authentication?

My server appears to be working properly but, what do I know, I am a newbie at LDAP?

Any help would be greatly appreciated.

---

### Post by newbie-user on 2009-12-30
Hi,

On your client machine, open /etc/ldap.conf and change your setting

# Another way to specify your LDAP server is to provide an
uri ldapi:///192.168.0.153:389

to 

# Another way to specify your LDAP server is to provide an
ldap://192.168.0.153


See if that works for you.

---

