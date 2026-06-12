---
title: "samba server problem"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by Ashishkhandelwal on 2010-02-11
I have installed samba server one month ago and it was working fine till yesterday but today morning when any network client is trying to access samba shared files by giving smb://<serveripaddress> it is asking for password...that is ok but when he is giving the password it is again opening the same password window to enter password again.The clients are giving correct password that is confirm.At the server side i have run smbclient -L localhost -U% and that is giving proper response so that also means that samba server is working fine so i dont know what could be the problem and what its solution.Can anybody help me in this regard.Thank you in advance.

---

### Post by johnson.d on 2010-02-18
You can probably try the following command from the client side:

```
$ smbclient -L <server-ip-address>
```

Can you also check if there is any duplicate ip-address in the network.

---

