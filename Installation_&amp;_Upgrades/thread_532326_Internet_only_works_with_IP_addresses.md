---
title: "Internet only works with IP addresses"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by IronArjen on 2007-08-22
I just installed Feisty keeping my home directory, starting from Dapper. The problem I encounter is that there is something really weird with the internet protocol. My Evolution cannot connect, Mozilla cannot connect. I can ping my IP as wel as the gateway with no problem

Then, I do hace access (have internet) when trying to work at pages that start with the actual IP address. For some reason some of my bookmarks had the IP address and these work and are fully functional.

What is wrong? Thanks

---

### Post by Einheit on 2007-08-22
Sounds like your DNS is down. Have you checked your network settings? Are DNS servers specified?

---

### Post by IronArjen on 2007-08-23
Thanks, indeed my DNS appears empty. The rather poor Informatics backup I have in the University works with windows and told me I shouldn't touch it. Anyway if I try to enter something, I cannot save it!

Any idea what I should enter and how?

---

### Post by IronArjen on 2007-08-23
Additonal info: I´ve got two DNS addresses now but they do not know where to enter them. In the network interface I cannot succesfully enter a DNS. I guess this is a configuration problem.
Where to specify the DNS addresses?

---

### Post by IronArjen on 2007-08-23
Looking at other posts I managed to figure it out although it was a bit strange. The DNS addresses need to be specified in a file resolv.conf within the etc folder. This file did not exist, a folder resolvconf did exist with a subfolder and a file that told me avahi could not be used??

I guess that Feisty comes for direct IP addresses, which I do not have. 

so the solution was

cd /
sudo gedit etc resolv.conf

In gedit append

nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

save file and logon!

Thanks for the DNS tip that helped solve the problem.

---

