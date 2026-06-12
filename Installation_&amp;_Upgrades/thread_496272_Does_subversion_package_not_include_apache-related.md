---
title: "Does subversion package not include apache-related setup"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by jcoles on 2007-07-08
I installed both apache 2.2 and subversion on 7.0.4, but it appears the two are not connected in any way. HTTP via mod-dav-svn is the most common way to access SVN. Not very useful without it. 

Does your version of subversion work with Apache 2.2 or 2.0? Where are mod-dav-svn and other required modules? 

I installed subversion and Apache 2.0 on another Linux distribution using the source tarballs. Debian package installation seems easy, but as you can't really see what is going on, it is hard to solve problems if the installation is not complete. 

What do I do after installing the apache2 and subversion packages? 

Would it be easier to just compile everything from tarballs?

---

### Post by jcoles on 2007-07-09
I guess I'll have to answer my own question.

The mod-dav-svn module is obtained like this:
sudo apt-get install libapache2-svn

(Why wouldn't it be a dependency of the subversion package?)

Not that this solves the problem, of course:

Setting up libapache2-svn (1.4.3dfsg1-1ubuntu1) ...
Enabling dav as a dependency
Module dav installed; run /etc/init.d/apache2 force-reload to enable.
Module dav_svn installed; run /etc/init.d/apache2 force-reload to enable.

# /etc/init.d/apache2 force-reload
No apache MPM package installed

I'll try removing Apache 2.0 and reinstalling Apache 2.2 from packages.

More later.

---

### Post by jcoles on 2007-07-09
Apache 2.2 installed, but cannot be started:

apache2: Syntax error on line 189 of /etc/apache2/apache2.conf: Syntax error on line 149 of /etc/apache2/httpd.conf: Cannot load /etc/apache2/modules/mod_auth_digest.so into server: /etc/apache2/modules/mod_auth_digest.so: cannot open shared object file: No such file or directory

apt-get knows nothing about mod_auth_digest

I tried commenting out the LoadModule line, only to find other missing dependencies. Each LoadModule line I deleted revealed another missing dependency:
/mod_authn_alias.so, /mod_authn_anon.so, mod_authn_dbm.so, mod_authn_default.so, /mod_authz_owner.so, on and on and on.

Any ideas? I don't even have a usable web server!
Debian package installation is just as bad as RPM packages, it leads to unfulfillable dependencies. 

Or have I somehow messed everything up so badly that I need to reinstall the whole system?

---

### Post by jcoles on 2007-07-09
Solved!

The problem seems to be the order of installation.

I completely removed subversion and apache and then reinstalled in this order:

* apache2, apache2.2-common, apache2-mpm-worker, apache2-utils
* libapache2-svn
* subversion, subversion-helper-scripts, subversion-tools

I had to add my configurations (in my case from a previous implementation) to the files in /etc/apache2. Some things have changed between Apache 2.0 and 2.2, but it was not hard to figure out.

It might be worth adding a note to the package description for subversion, that if you want HTTP access, you need to install apache2 and libapache2-svn first.

---

