---
title: "Using LDAP HomeDir for users in netgroups"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by sherrera on 2013-05-22
Hello,
We are currently moving away from Solaris and into the ubuntu world. We have an ldap server that hosts netgroups and use these netgroups for login administration. That part i have working. My ubuntu box will query the netgroup and knows which users are allowed. I did that with the nsswitch.conf file.  What I can't figure out is how to make the ubuntu server look at the home directory entry for the netgroup on the LDAP server and apply that when the user logins in. The LDAP entry for a user contains HomeDir: test /home1/j/jsmith. Test being the name of the netgroup. The default is /home/USER but since we have a few thousand users it would be great to do something like /home1/j/jsmith  That is how it is set up in the solaris side.  If anyone knows of an easier way to accomplish this, i'm open to suggestions. 

Thanks

---

