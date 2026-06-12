---
title: "No Internet Access After Hardy Upgrade"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by uhhuhuhhuh on 2008-04-22
[update: the issue ended up being the ipv6 setting within firefox. funny how that post-upgrade sense of panic really can make you over look the smaller things..]

I Just upgraded to Hardy from Gutsy, and it seems that I'm unable to connect to the internet using either ethernet or wireless--it seems to be telling me that I am connected to the network but I can't actually pull anything up in a browser.  Any ideas on what I'm missing?

Thanks!

---

### Post by hannah187 on 2008-04-23
Well I have got similar problem. Try starting the browser and then go to anysite with their IP address and see if you can get connected. If this is true then under Manual Network Configuration, Under DNS tab you need to add in your DNS server IP address.

---

### Post by stream303 on 2008-04-23
If you are having to add your dns addresses manually, and you are behind a router, the easiest cure is to put your isp's primary and backup dns server addresses *inside the router's setup page,* and either restart networking or just reboot.

I prefer to use the OpenDNS addresses seen on the bottom right of their page:

[http://www.opendns.com](http://www.opendns.com)

---

### Post by uhhuhuhhuh on 2008-04-25
Well, it's definitely an issue with the DNS--I am able to visit sites using IP addresses but that's it.  My connection information reports the right DNS servers, and I put them into my router's setup page as well.  I'm still getting the same problem.  I tossed in an old livecd(7.04) and had no problem, but the Hardy upgrade is still confusing my computer.  Anything else I can try?

Thanks again!

---

