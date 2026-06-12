---
title: "preseed question --"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by uonedang on 2010-04-06
Hi folks,
 
I tried to make the installation image (Karmic amd64) with preseed file (unattended installation) ..
 
I currently have 2 issues:
 
1) I can not configure the system with static IP address, diasble the DHCP client ... 
I have included the following in the preseed file:
 
*d-i netcfg/disable_dhcp boolean true*
*d-i netcfg/get_nameserver ...*
*d-i netcfg/get_ipaddress ...*
*d-i netcfg/get_netmask ...*
*d-i netcfg/get_gateway ...*
*d-i netcfg/confirm_static boolean true*
 
2) I can not get the late_command working ... a simple test late_string was included in the pressed file: 
 
*d-i preseed/late_command string in-target cp /usr/bin/abc /usr/bin/abc_copy*
 
Is there something that I have incorrectly configured above ?
 
Any suggestion ?
 
Thanks
 
Dang

---

