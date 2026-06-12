---
title: "Shared folder problem"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sircrayons on 2009-04-12
I have three computers, one with 9.04 beta, and two with 8.10.  All three are wireless to the same router, and are all configured to use DHCP.  On the desktop that's running 8.10, I have a Samba share that my laptop (also running 8.10) can access.  Both of those machines can see every shared resource on my network when browsing the Network.  However, they can not see my desktop running 9.04, nor can it see them.  Even my shared folder is invisible to this machine.  The Windows Workgroup name is correct, and I can't see anything else that might be wrong.  It's a fresh install of 9.04.  I've barely done anything to it yet.  Help!

---

### Post by superprash2003 on 2009-04-13
are the machines able to ping each other , have you tried accessing the shares by typing smb://x.x.x.x where x.x.x.x is the ip of the 9.04 machine

---

### Post by bacardiandwatermelon on 2009-04-16
I had a issue with the samba gui in Nautalus.. I could never get the share to work properly. However editing the /etc/samba/smb.conf got the share up and running for me...

---

