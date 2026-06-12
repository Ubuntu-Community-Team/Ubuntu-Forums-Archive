---
title: "Ati Catalyst 12.3"
date: 2012-04-05
forum: Installation &amp; Upgrades
---

### Post by DjDiabolik on 2012-04-05
Hi boys.. i have a Ati Catalyst 12.3 !! I have stay from two days to try to install correctly latest AMD Driver but i can append.

I have read so many guide over internet... on the last try i have used this:
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

But after i all complete all i reboot but the driver it's no correctly installed:
```
diabolik@Diabolik-ubuntu:~/catalyst12.3$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13
```

I have installed Ubuntu 11.10 and i have complete all upgrade.........and after the upgrade i obtain this kernel:
```
diabolik@Diabolik-ubuntu:~/catalyst12.3$ uname -r
3.0.0-18-generic-pae
diabolik@Diabolik-ubuntu:~/catalyst12.3$ 
```

I don't know if it's correct but this kernel it's been installed automatically from software updater included on ubuntu....... please help me with this installation.

---

### Post by aeronutt on 2012-04-05
What CPU and GPU do you have?  FYI, catalyst/fglrx doesn't work for me under 11.10, but does (mostly) under 12.04 beta.

---

### Post by DjDiabolik on 2012-04-05
CPU it's a AMD64 X2 4400+ and GPU it's a Ati HD4650.
Motherboard it's a M2N68-Plus with latest bios.

I dont know if this driver work..... but i don't know if i need to install fglrx when i want to install Ati 12.3 Driver.

I try everythings but nothing working :(

---

