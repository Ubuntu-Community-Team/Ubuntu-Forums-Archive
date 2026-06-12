---
title: "Cannot upgrade to 11.04 errors"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by towin314 on 2011-05-04
I receive the following errors every time the upgrade option appears and cannot get past it.  Is there a better way or something else I can try?  

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by lechien73 on 2011-05-04
Hello & welcome to the forums :)

You could be experiencing a routing issue. Sometimes Network Manager will make the router the default DNS server - even if the router doesn't forward DNS requests. You can test this by:

[LIST=1]
[*]Edit the network connection in **Network Manager**
[*]Click on the **IPV4 Settings** tab
[*]Change the method from **Automatic (DHCP)** to **Automatic (DHCP) addresses only**
[*]Supply the Google Public DNS servers in the DNS fields: **8.8.8.8** and **8.8.4.4** - or your ISP DNS settings if you know them
[*]Save & test again :)
[/LIST]

HTH

---

### Post by towin314 on 2011-05-08
Thanks lechien73 that worked perfectly.

---

### Post by mörgæs on 2011-05-08
Good, please mark the thread 'solved'.

---

