---
title: "apt-get update/upgrade &quot;Protocol http not supported or disabled in libcurl&quot; ...solved"
date: 2014-09-25
forum: Installation &amp; Upgrades
---

### Post by sanderj on 2014-09-25
Using "sudo apt-get update && sudo apt-get upgrade", I repeatedly got:

```
Ign https://get.docker.io docker/main Translation-en_US                        
Ign https://get.docker.io docker/main Translation-en                           
Err https://get.docker.io docker/main amd64 Packages                           
  Protocol http not supported or disabled in libcurl
Err https://get.docker.io docker/main i386 Packages                            
  Protocol http not supported or disabled in libcurl
W: Failed to fetch https://get.docker.io/ubuntu/dists/docker/main/binary-amd64/Packages  Protocol http not supported or disabled in libcurl

W: Failed to fetch https://get.docker.io/ubuntu/dists/docker/main/binary-i386/Packages  Protocol http not supported or disabled in libcurl

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Workaround:

I changed /etc/apt/sources.list.d/docker.list to contain

```

#deb https://get.docker.io/ubuntu docker main
deb http://get.docker.io/ubuntu docker main

```

and solved the error message.

HTH

---

