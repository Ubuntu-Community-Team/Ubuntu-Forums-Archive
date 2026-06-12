---
title: "Issue with Samba authentication following upgrade"
date: 2021-12-03
forum: Installation &amp; Upgrades
---

### Post by BestLinuxDistro on 2021-12-03
I have around 30 Ubuntu 20.04 desktops. They authenticate samba through  ADS. Any of them that have applied updates takes the version of Samba to  4.13.14. Anyone who hasn't applied the update is still on 4.11.6 and  this works fine. The problem I have is that I am new to the company and  the person who set this up has left so I don't have too much knowledge  of the setup. The error log within /var/log/samba is this;

[2021/12/03 10:27:46.719165,  0] ../../source3/auth/auth_generic.c:125(auth3_generate_session_info_pac  )
  auth3_generate_session_info_pac: winbindd not running - but required as domain member: NT_STATUS_NO_LOGON_SERVERS

The issue here [https://ubuntuforums.org/showthread....275&p=14068432]("https://ubuntuforums.org/showthread.php?t=2469275&p=14068432")  seems to be very similar but there is no resolution to this. I have  tried to install winbind as it wasn't installed previously but now i get  an authentication error when trying to log in. On the desktop I can run  commands like realm discover and id and they return information from  the domain controller. 

I understand this is pretty vague but if someone could point me in a direction to go with this i would be very grateful.

---

### Post by rsteinmetz70112 on 2021-12-03
Samba has two basic ways in implementing ADS, one with built-in DNS and LDAP and another using standalone programs for BIND LDAP. First I'd try to determine which method was used. 

I'm afraid I can't be much help I'm not that familiar with the ADS set-up. If no one comes along with better information I'd suggest you check out the samba mailing list. They are very knowledgeable, helpful and patient.

---

