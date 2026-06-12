---
title: "ubuntu 11.10 64-bit PC server installation on Dell T710 tower machine"
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by UvarajT on 2012-01-06
Hi,
 
I installed ubuntu 11.10 64-bit server setup in a Dell T710 Tower machine.
[http://www.dell.com/us/enterprise/p/poweredge-t710/pd](http://www.dell.com/us/enterprise/p/poweredge-t710/pd)
 
Installation was smooth. After installation i tried to update the machine using,
sudo apt-get update [This command was success]
sudo apt-get upgrade [This commad failed with the below error]
 
*Error encountered Setting up crossplatformui:i386*
*E: sub-process /usr/bin/dpkg returned an error code (1)*
 
And I tried to install bridge utils,
sudo apt-get install -y bridge-utils [even this command failed with the above error]
 
regards,
Uva

---

