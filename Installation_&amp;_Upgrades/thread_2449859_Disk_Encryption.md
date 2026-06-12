---
title: "Disk Encryption"
date: 2020-09-03
forum: Installation &amp; Upgrades
---

### Post by Adam_Barnett on 2020-09-03
Hi, 

I am installing Ubuntu using the automated installed for 20.04. 
I am trying to secure it but at the same time make it user friendly.  

If i encrypt the whole disk during the install phase then the user need to do the following: 

- Enter encryption key to boot up
- Enter username and password to login
- Then enter username and password to access VPN

it seem a lot of entering username and password. Is there a way to stream line it a bit. 
For example on OSX when encrypted the user just enters their username and password and they decrypt and login all in one, is there way to this on Linux

Thanks

---

### Post by sudodus on 2020-09-03
You can install Ubuntu (or modify it after installation) so that you need not log in with a password. In other words, the second item in your list can be skipped.

---

### Post by TheFu on 2020-09-03
> **Adam_Barnett said:**
>  
- Enter encryption key to boot up
- Enter username and password to login
- Then enter username and password to access VPN
 

Each of those things is unrelated.  They aren't tied to the same userid.  Tying them to the same userid would drastically reduce security.

For an openvpn connection, you can place the login credentials into a file and use the config to access it. In the .ovpn config, use:
```
auth-user-pass /etc/openvpn/login.cf
```
Inside the login.cf
there are 2 lines - the username and the password. username= or userid: or anything like that, just the plain text for each, on line 1 and line 2.  Both these files should be locked down through root:root 600 permissions.

---

