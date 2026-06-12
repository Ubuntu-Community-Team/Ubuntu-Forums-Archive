---
title: "CVS installation and configuration"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by Ashishkhandelwal on 2010-01-16
Hello everyone

I have been given a task to install and configure CVS(Control Version system) on linux server in such a way that every user with a user id and password in the network should be able to connect to CVS server where all code resides.Can anyone tell me the steps by which i can install and configure CVS to fulfill my boss requirement.

Thank you in advance.

---

### Post by spamalam on 2010-01-16
First up, I'm going to assume CVS is mandatory.  If you have the option, get rid of it as its rather redundant and replaced by a plethora of leaner, meaner solutions.  You should use a more modern technology, subversion is the easiest port but there's systems such as mercurial, git, etc. that are far superior to CVS.

If you can use subversion, setting up LDAP + apache is a doddle:
[http://blogs.open.collab.net/svn/2009/03/subversion-with-apache-and-ldap-updated.html](http://blogs.open.collab.net/svn/2009/03/subversion-with-apache-and-ldap-updated.html)

Sepcifically on CVS. You can use LDAP for CVS authentication:
[http://riteshmajumdar.blogspot.com/2007/11/cvs-as-central-repository-server.html](http://riteshmajumdar.blogspot.com/2007/11/cvs-as-central-repository-server.html)

Following that guide should get you what you want.  users will then be managed in LDAP.


Here's a plethora of reasons for ditching CVS in favour of subversion:
[http://versioncontrolblog.com/comparison/CVS/Subversion/index.html](http://versioncontrolblog.com/comparison/CVS/Subversion/index.html)

---

