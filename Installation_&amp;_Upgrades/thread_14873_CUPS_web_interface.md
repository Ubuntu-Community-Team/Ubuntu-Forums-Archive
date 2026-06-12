---
title: "CUPS web interface"
date: 2005-02-10
forum: Installation &amp; Upgrades
---

### Post by yarook on 2005-02-10
Hallo

  When I try to use CUPS web interface I get the following message:
*  Administrative tasks have been disabled for security reasons. Please use Menu Computer > System configuration > Printing.*
  Is there a way to bypass this restriction and to enable the web interface?
Thanks in advance
Petar

---

### Post by grj on 2005-02-10
Check your settings in the /etc/cups/cupsd.conf

I believe the last section handles admin security 

<Location /admin>
#
# You definitely will want to limit access to the administration functions.
# The default configuration requires a local connection from a user who
# is a member of the system group to do any admin tasks.  You can change
# the group name using the SystemGroup directive.
#

AuthType Basic
AuthClass System

## Restrict access to local domain
Order Deny,Allow
Deny From All
Allow From 127.0.0.1

#Encryption Required
</Location>

---

### Post by m4ng0 on 2005-02-10
You can also try:
sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart

---

### Post by kultex on 2005-02-11
I had the same problem

set a root password  and login with root and the password - it functions \\:D/

---

### Post by yarook on 2005-02-11
It works now. 
Thanks for the help.
Petar

---

### Post by grj on 2005-02-11
What did you do to fix it?

---

### Post by yarook on 2005-02-12
I've enabled the root acces for CUPS web interface with:
[I]sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart[/I]
Petar

---

