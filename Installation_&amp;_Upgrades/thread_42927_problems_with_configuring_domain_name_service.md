---
title: "problems with configuring domain name service"
date: 2005-06-20
forum: Installation &amp; Upgrades
---

### Post by frank_y on 2005-06-20
I recently installed hoary ubuntu and I got internet to work, and dns to work. However, dns lookup was incredibly slow and I also think internet is a bit slower than usual also.

I checked the network administration thing and I tried adding lots of DNS ip's but it didnt' work.

Now, I reset it to the two dns server ips and the one search dns thing which it originally started with. Can anybody help me get dns working?

Frank

---

### Post by diebels on 2005-06-20
[QUOTE=resolv.conf]nameserver *.*.*.*
nameserver *.*.*.*
options rotate
options timeout:1
options attempts:3
[/QUOTE]
The options could speed it up a bit. You don't  need the search thing. And disable ipv6 in "firefox about:config"

---

### Post by frank_y on 2005-06-20
Nevermind, It seems to work fine now that I just found a faster nameserver. Really, I have no idea why it works fast now.

128.242.141.2

It's the DNS of some automotive company and it seems to work well.

Thanks,

Frank

---

