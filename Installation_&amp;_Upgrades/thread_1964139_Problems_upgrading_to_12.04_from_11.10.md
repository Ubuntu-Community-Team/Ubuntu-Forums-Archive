---
title: "Problems upgrading to 12.04 from 11.10"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by littlechasa7 on 2012-04-23
I'm trying to use the update-manager -d command to upgrade to 12.04, as the Ubuntu website told me to do, but when the installer is setting up software channels it comes up with this error:

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources)  404  Not Found [IP: 91.189.92.177 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.92.177 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources)  404  Not Found [IP: 91.189.92.177 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.177 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.


It tells me there may be a problem with my network, but that appears fine. I'm not sure why it would be sending me to a karmic website that was archived by canonical either.

Thanks!

---

### Post by cortman on 2012-04-23
All karmic repositories can/should be removed. Run

```
gksu gedit /etc/apt/sources.list
```

and delete all lines with karmic references.

---

### Post by marin123 on 2012-04-23
What mirror are you using? Try Main server and see if the same error comes up.

---

### Post by ajgreeny on 2012-04-23
All support for karmic (9.10) disappeared a while ago, so those lines have not been any use for some time.

Do what cortman says and you should be fine.

---

