---
title: "Problem upgrading"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by andleg on 2010-07-25
From a few days, after a fileSystem problem solved with fsck
When I want to upgrade, if do :
apt-get update
apt-get upgrade.

It starts well and the bocks for ever on :
(Reading database ...
Any help welcome

Andre

root@a-laptop:~]> apt-get upgrade                                                                                                                                                                                    
Reading package lists... Done                                                                                                                                                                                                     
Building dependency tree                                                                                                                                                                                                          
Reading state information... Done                                                                                                                                                                                                 
The following packages have been kept back:                                                                                                                                                                                       
  linux-generic linux-headers-generic linux-image-generic                                                                                                                                                                         
The following packages will be upgraded:                                                                                                                                                                                          
  apt apt-transport-https apt-utils base-files firefox firefox-3.0 firefox-3.5 firefox-3.5-dbg firefox-3.5-dev firefox-3.5-gnome-support firefox-branding firefox-dbg firefox-dev firefox-gnome-support grub-common               
  libgssapi-krb5-2 libk5crypto3 libkrb5-3 libkrb5support0 linux-libc-dev sreadahead ureadahead xulrunner-1.9.2                                                                                                                    
23 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.                                                                                                                                                                   
Need to get 0B/89.3MB of archives.                                                                                                                                                                                                
After this operation, 283kB of additional disk space will be used.                                                                                                                                                                
Do you want to continue [Y/n]? Y                                                                                                                                                                                                  
(Reading database ...

---

### Post by andleg on 2010-07-25
I just find out that (Reaading database...

is coming from dpkg command.
How can I download dpkg sourcecode to find out wher in the code we stay stucked.. And if possible why and finally find a solution??

Merci

---

