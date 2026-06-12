---
title: "Broken Package gufw"
date: 2014-10-20
forum: Installation &amp; Upgrades
---

### Post by Herb_Lee on 2014-10-20
apt-get install gufw throws a "Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main libgudev-1.0-0 amd64 1:204-5ubuntu20.6
  404  Not Found [IP: 91.189.91.13 80]".  (  "E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libgudev-1.0-0_204-5ubuntu20.6_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libgudev-1.0-0_204-5ubuntu20.6_amd64.deb)  404  Not Found [IP: 91.189.91.13 80]")

Looking at us.archive.ubuntu.com/ubuntu/pool/main/systemd, it appears that "...ubuntu20.7..." is present.  Is 20.6 still current and got dropped accidentally or does the package dependency need to be updated?  Also noted this same issue with a wireshark install.

Thanks!

---

### Post by Frogs Hair on 2014-10-20
Hello Herb_Lee:

Run the update manager to refresh the repository list and try again.

---

### Post by Herb_Lee on 2014-10-21
works now, thanks!

---

### Post by mörgæs on 2014-10-21
Good, please mark the thread 'solved'.

---

