---
title: "Synaptic cannot connect, whislt internet works"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by retrodans on 2011-05-02
When I run sudo apt-get update I get several lines with things such as:

```
Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
```

This was happening whilst I was setting up a new machine, but then, when I went to an ubuntu machine which was already working, I now get the same issue there.  Are there issues with certain servers I should be checking status logs for?

Not sure the issue is local, as happened on a pre-existing machine, so has anyone else got this at the moment?

Cheers,
Dan

---

### Post by lechien73 on 2011-05-02
I suppose it's possible that there are issues with the GB servers - have you tried setting the download source to "Main Server" in Software Sources (now accessible via the Ubuntu Software Centre, then Edit -> Software Sources)?

If that still doesn't work, then it could be a router issue. Sometimes Network Manager will make the router the default DNS server - even if the router doesn't forward DNS requests. You can test this by:

[LIST=1]
[*]Edit the network connection in **Network Manager**
[*]Click on the **IPV4 Settings** tab
[*]Change the method from **Automatic (DHCP)** to **Automatic (DHCP) addresses only**
[*]Supply the Google Public DNS servers in the DNS fields: **8.8.8.8** and **8.8.4.4** - or your ISP DNS settings if you know them
[*]Save & test again :)
[/LIST]

HTH

---

### Post by poodoopealeoaph on 2011-05-02
or another thing to check... make sure you dont have updates to run.

---

### Post by retrodans on 2012-04-16
I know this has been some time, but I am just going through checking some old posts.  As suggested, it was that there was a problem with the server.  After being patient and trying again later, it worked fine.

---

