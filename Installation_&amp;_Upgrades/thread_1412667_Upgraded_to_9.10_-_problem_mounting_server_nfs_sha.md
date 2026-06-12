---
title: "Upgraded to 9.10 - problem mounting server nfs shares"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by svsig on 2010-02-21
Hi.

I have just upgraded to version 9.10 on my Ubuntu desktop machine. I have a server that is still version 9.04. 

After the upgrade my desktop machine is unable to mount the nfs shares on my server that are defined in the /etc/fstab file.

I have tried searching for a solution, but I have not been able to find anything about this. Can somebody please help me?

Regards,
Sveinung

---

### Post by suseendran.rengabashyam on 2010-02-22
Hi,

A similar thread
[http://ubuntuforums.org/showthread.php?t=1329355](http://ubuntuforums.org/showthread.php?t=1329355)

Hope this helps.

---

### Post by svsig on 2010-02-22
Hi.

Thanks for your reply. 

I managed to solve the problem myself, it was only DHCP that played a trick on me. I obtain IP addresses via DHCP, and up to now every machine has always got the same IP address. I have defined the machines in the /etc/hosts file on the server and granted privileges to each machine name in the /etc/exports file. When the IP address on one machine changed this machine lost its privileges. When I changed the IP address in the hosts file on the server the problem was solved.

But I think I will have to do something about the way my machines obtain their IP addresses.

---

