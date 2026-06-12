---
title: "Way to get apt-get work past firewall"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by Saubazi on 2006-10-12
I am toying with the idea to replace SuSe rubbish with Ubuntu on my second work-PC. However, Ubuntu is rather apt-get dependent and I'd also like to employ this feature but the problem is that the internet access is blocked by firewall. I know how to configure browser so that it will ask for proxy password and so on and I know what to type in - I just don't know how I can get apt-get to work with this information - anyone, anyone?

---

### Post by JonahRowley on 2006-10-12
Look at the apt.conf manpage.  Search for "proxy" (hit slash, type proxy).  Here's the first paragraph:

```

       http   HTTP URIs; http::Proxy is the default http proxy to use.  It  is
              in the standard form of http://[[user][:pass]@]host[:port]/. Per
              host  proxies  can  also  be  specified  by   using   the   form
              http::Proxy::<host>  with  the special keyword DIRECT meaning to
              use no proxies. The http_proxy environment variable  will  over&#8208;
              ride all settings.

```

---

