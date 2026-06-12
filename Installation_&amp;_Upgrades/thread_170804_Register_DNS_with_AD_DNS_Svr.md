---
title: "Register DNS with AD DNS Svr?"
date: 2006-05-05
forum: Installation &amp; Upgrades
---

### Post by atatistcheff on 2006-05-05
Is there a way to have an Ubuntu machine register it's DNS name with an Active Directory DNS server without using DHCP?  I have static IP machines that I need to register.  There is a check box in a Windows XP client to do this even if you're using a static IP.  Is there a setting somewhere in Ubuntu I can change to allow that?  These are not domain members which may (should) be a security issue with this.

Thanks,
Alex

---

### Post by funky_D on 2007-09-04
hello everybody,
i need to do the same... i need to register a ubuntu machine with static IP in a DNS Server.
is it possible??

many thanks

---

### Post by mcsween on 2007-09-24
I'm having the same issue...need my STATIC Ubuntu servers register their DNS with active directory.  I have secure only updates turned off in AD

---

### Post by aglide on 2007-09-25
I'll add myself to the list of people wondering how to do this. Anyone?

---

### Post by kingpoiuy on 2007-12-06
Yes, Add me to this issue also!

---

### Post by naitram on 2007-12-07
I'm sure there's a way to do it graphically....

/etc/dhclient.conf

send host-name "desired.host.name";

reinitialize your net scripts and it should go for you.

---

### Post by kingpoiuy on 2007-12-10
Thank you for the reply.  

Problem is that the dhcp file you talk about is for DHCP and we are trying to send our client name while using a static address.  I have the dhcp3 file setup as you specified and it works on my dynamic maching but the machine next to it is static and it doesnt work.

---

### Post by davidshere on 2008-07-09
Any resolution to this problem after two years?  Windows machines do this automatically, and there is a command to do it manually, too -- "ipconfig /registerdns".  Surely Linux has an equivalent command.

---

