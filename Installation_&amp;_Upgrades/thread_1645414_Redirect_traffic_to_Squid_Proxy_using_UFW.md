---
title: "Redirect traffic to Squid Proxy using UFW"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by PharcydeWolf on 2010-12-14
Hi everyone.

I realize that this may be an old topic, however after hours of searching on Google and Ubuntuforums, I have not been able to come up with a DEFINITE solution.

I am currently using Ubuntu Server edition 10.04 LTS. I have already setup Squid as my proxy server and it is working without problems. I have also configured UFW and it is also working without problems.

One of the few modifications I have performed to UFW has been masquerading to be able to share my server internet connection with other computers and it is also working properly.

On previous installations I have performed port forwarding using another OS. I was able to redirect *ALL OUTBOUND* traffic to my Squid Proxy server. I was then able to use my ACL on Squid to deny or allow traffic depending on certain rules. I have been unable, though, to accomplish this using UFW.

As far as I can tell, I need to modify the before.rules file for UFW to set up port redirection but as to date, I have been unable to accomplish this. My Squid proxy is running on default port 3128 and eth0/eth1 corresponds to my WAN/LAN connection accordingly.

If anyone has done this, could you share your solution?

Thanks in advance.

---

