---
title: "LDAP,NIS,Kerberos (ADCU for Linux)"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by kwadman on 2009-12-09
Hello ubuntu forum,

I require some help.  I wish to setup a network that works like windows but for with lunix of course!.  It will need to be able to handle security/DNS/DHCP & Document store from one location.

The prolem is I am a complete beginner.

I know two commands (ls & sudo apt-get.....)

I've been doing some reading and have found that I think I need to be using one of the following:
LDAP
NIS
Kerberos

I have looked at a few Linux based OS's.  I did notice that when you install fedora live desktop it gives you the option to connect to one of the above.

So I am looking for a complete solution.
1. How to setup ubuntu to act as server for my needs (or other Linux build)

2. Add ubuntu machine to server to use new security settings. (or other  linux build)


Someone please help ! - I wish to learn!!

---

### Post by adaucourt on 2009-12-09
> **kwadman said:**
> Hello ubuntu forum,

I require some help.  I wish to setup a network that works like windows but for with lunix of course!.  It will need to be able to handle security/DNS/DHCP & Document store from one location.

The prolem is I am a complete beginner.

I know two commands (ls & sudo apt-get.....)

I've been doing some reading and have found that I think I need to be using one of the following:
LDAP
NIS
Kerberos

I have looked at a few Linux based OS's.  I did notice that when you install fedora live desktop it gives you the option to connect to one of the above.

So I am looking for a complete solution.
1. How to setup ubuntu to act as server for my needs (or other Linux build)

2. Add ubuntu machine to server to use new security settings. (or other  linux build)


Someone please help ! - I wish to learn!!

You are gonna have to read a whole lot...

File and Print Sharing
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

LDAP
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

NIS
[https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)

DHCP
[https://help.ubuntu.com/7.04/server/C/dhcp.html](https://help.ubuntu.com/7.04/server/C/dhcp.html)

---

### Post by kwadman on 2009-12-09
If I do the lot i will have my result?

is there anything else I need.

Could you just explain what each bit does.

I know DHCP, - releasing IP addresses to client machines.

But NIS?? whats this compared to windows?

---

### Post by adaucourt on 2009-12-11
> **kwadman said:**
> If I do the lot i will have my result?

is there anything else I need.

Could you just explain what each bit does.

I know DHCP, - releasing IP addresses to client machines.

But NIS?? whats this compared to windows?

if you just need dhcp dns and file print sharing no need for nis or ldap.  if you plan on interfacing with windows domain you may want to integrate with ldap

---

### Post by 480silverton on 2010-01-12
Warning.
If you go with the NIS version.
There is an incorrect step in setting up the server that screws everything up.

---

