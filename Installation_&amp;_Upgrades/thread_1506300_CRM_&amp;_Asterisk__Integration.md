---
title: "CRM &amp; Asterisk  Integration"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by Mallikarjun Kalsure on 2010-06-10
hi, all ,, I am installed  CRM Vtiger & Asterisk Server , but i can;t get a call from CRM Vtiger ....these are changes in manager.conf....

[general]
enabled = yes
port = 5038
 
bindaddr =172.16.1.129

[admin]
secret=admin
deny=0.0.0.0/0.0.0.0
permit=172.16.1.0/255.255.255.0
read=system,call,log,verbose,command,agent,user
write=system,call,log,verbose,command,agent,user

[2003]
secret=2003
deny=0.0.0.0/0.0.0.0
permit=172.16.1.0/255.255.255.0
read=system,call,log,verbose,command,agent,user
write=system,call,log,verbose,command,agent,user

this is my file.. manager.conf.. anything new changes?????

---

