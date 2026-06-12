---
title: "ntp package not found on apt-get install"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by deanhiller on 2010-01-22
I am using the last LTS version(i think 8.04) and when I run apt-get install ntp, I get the following error..

  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ntp/ntp_4.2.4p4+](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ntp/ntp_4.2.4p4+)
dfsg-3ubuntu2.2_amd64.deb  404 Not Found [IP: 91.189.88.30 80]
root@new:~# ping 91.189.88.30

i see plenty of other packages in that dir that don't quite match.  how do I fix this so i can get ntp on my server?

thanks,
Dean

---

### Post by n0dix on 2010-01-22
Try to run:
```
sudo aptitude update
sudo aptitude upgrade
```

---

