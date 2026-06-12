---
title: "Samba Stops working after upgrade to 18.02 Part II"
date: 2019-02-24
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2019-02-24
I thought I had resolved my problem in the earlier post, However I have an additional problem. No users can login. Windows reports there is no path to the shares and that is cannot access the member server.

wbinfo -u works and gives a list of all users

getent passwd does not show any remote users of the PDC

I have rejoined the domain with net join -U administrator

The PDC is running Samba Version Version 4.3.11-Ubuntu
The member server is running 4.7.6-Ubuntu

---

### Post by rsteinmetz70112 on 2019-02-24
I think I've solved this problem 

Apparently when upgrading from 16.04 to 18.04 libpam-winbind and libnss-winbind were not installed.
I'm pretty sure they were on the 16.04 install and should have been upgraded, in any event I think they should be dependencies of winbind and should have been installed.

---

