---
title: "Failure to fetch sharing device"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by tim042849 on 2011-11-03
From ubuntu 10.04, when I go to add the sharing device, I get the following error messages:
```

W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.4.7~dfsg-1ubuntu3.7_i386.deb
  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/libpam-smbpass_3.4.7~dfsg-1ubuntu3.7_i386.deb
  404  Not Found [IP: 91.189.92.166 80]

```
Internet connections looks good. Is there a respository that needs to be added?
Is so, which?
thanks

---

### Post by tim042849 on 2011-11-03
This has been solved. I first pointed my browser to the url for the device. It was not found
by the browser. I then removed the name of .deb file from the end of the URL and sent
that request. I was then given a directory of file listings and surmised that what I really
needed to do first was to run update manager. This particular machine is used only
intermittently. After running update manager, I was able to install the sharing device (samba),
because a new URL was (I assume) provided.

---

