---
title: "extras.ubuntu.com 404  Not Found"
date: 2015-05-01
forum: Installation &amp; Upgrades
---

### Post by alpage2 on 2015-05-01
After a clean install of lubuntu 15.04, when I run sudo apt-get update, the extras repository does not respond. The response in my terminal was:

```

Err http://extras.ubuntu.com vivid/main Sources                                
  404  Not Found
Err http://extras.ubuntu.com vivid/main i386 Packages                          
  404  Not Found

---snip---

Fetched 237 kB in 27s (8,596 B/s)                                              
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/vivid/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

This has happened more than once, over several days.

Is there a problem with this repository?

Thanks
Alan

---

### Post by Dennis N on 2015-05-01
Apparently there is no section for Vivid at present. Maybe coming later? See for yourself:

[http://extras.ubuntu.com/ubuntu/dists/](http://extras.ubuntu.com/ubuntu/dists/)

---

### Post by alpage2 on 2015-05-01
Thanks Dennis

Mystery solved!  ;)

---

