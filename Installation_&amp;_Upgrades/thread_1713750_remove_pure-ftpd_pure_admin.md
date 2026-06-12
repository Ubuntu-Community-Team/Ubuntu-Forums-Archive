---
title: "remove pure-ftpd pure admin"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by spindler on 2011-03-24
I am having problems troubleshooting my pure-ftpd setup.  I am always getting a 530 authentication error.

I attempted to correct the problem by doing the following:

# pure-pw mkdb
# ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/PureDB
# gedit /etc/pure-ftpd/conf/PAMAuthentication
               Change yes into no

# /etc/init.d/pure-ftpd stop
# /usr/sbin/pure-ftpd -j -lpuredb:/etc/pure-ftpd/pureftpd.pdb &
# /etc/init.d/pure-ftpd start


This create a new error.   

421 Unable to read the indexed puredb file (or old format detected) - Try pure-pw mkdb

I am getting a feeling this is getting from bad to worse.   I attempted to remove pure-ftpd and pureadmin to start over again.  However, it appears I cannot remove everything.  I attempted the following:

apt-get remove pure-ftpd pureadmin

I am not sure what this really does because I can still see the folder /etc/pure-ftpd  and I cannot remove it.

I could not use rm /etc/pure-ftpd  because the system said it was not empty.

I also tried sudo aptitude remove pure-ftpd pureadmin .  Again I cannot completely remove the folder.

**How do I completely remove pure-ftpd and pure admin and all databases, files and folders so I have a fresh system ready to start the install again?**

**Any idea how to solve a 530 Authentication error? I am using an external IP address through Filezilla. **

---

### Post by Amarsa on 2011-04-29
use 'rm -r /etc/pure-ftpd' command

---

