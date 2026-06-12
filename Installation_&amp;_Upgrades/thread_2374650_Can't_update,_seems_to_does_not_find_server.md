---
title: "Can't update, seems to does not find server"
date: 2017-10-17
forum: Installation &amp; Upgrades
---

### Post by a_guenther on 2017-10-17
Hi,
I have since a while problems updating. I am running Kubuntu 17.04.

I always get the message it would not find the repositories:

```
E: Fehlschlag beim Holen von http://archive.ubuntu.com/ubuntu/dists/zesty/main/binary-armhf/Packages  404  Not Found [IP: 91.189.88.162 80]
E: Fehlschlag beim Holen von http://archive.ubuntu.com/ubuntu/dists/zesty-updates/main/binary-armhf/Packages  404  Not Found [IP: 91.189.88.162 80]
E: Fehlschlag beim Holen von http://archive.ubuntu.com/ubuntu/dists/zesty-backports/main/binary-armhf/Packages  404  Not Found [IP: 91.189.88.162 80]
E: Fehlschlag beim Holen von http://archive.ubuntu.com/ubuntu/dists/zesty-security/main/binary-armhf/Packages  404  Not Found [IP: 91.189.88.162 80]
```

I changed already in muon the mirror and removed 3rd party entries, without success. Updating through muon or sudo apt-get upgrade would always fail with this error message. Due to this, I seem to get also no automatic updates anymore.
Any ideas? Probably should install Kubuntu 17.10 once it is released anyways from scratch instead of upgrading, I might have dragged too much old stuff for too long, but would still be nice to fix this.

Thanks!

---

### Post by ian-weisser on 2017-10-17
404 is the http code: File Not Found on this server.
Try it yourself: Open any of those URLs in your favorite browser.

[http://archive.ubuntu.com/ubuntu/dists/zesty/*/](http://archive.ubuntu.com/ubuntu/dists/zesty/*/) do exist, but a binary-armf subdirectory within does not.
Your source URLs seem to be invalid.

See [https://askubuntu.com/questions/705895/how-to-fix-a-failed-to-fetch-binary-armhf-packages-error-during-apt-get-update](https://askubuntu.com/questions/705895/how-to-fix-a-failed-to-fetch-binary-armhf-packages-error-during-apt-get-update) for two solutions.

---

### Post by QIII on 2017-10-17
Hello!

Are you running Kubuntu on an ARM device?

---

### Post by a_guenther on 2017-10-17
> **QIII said:**
> Hello!

Are you running Kubuntu on an ARM device?
No, it's a PC (64bit), and indeed, I have no idea how the arm slipped in...

[QUOTE=ian-weisser]404 is the http code: File Not Found on this server.
Try it yourself: Open any of those URLs in your favorite browser.

[http://archive.ubuntu.com/ubuntu/dists/zesty/*/](http://archive.ubuntu.com/ubuntu/dists/zesty/*/) do exist, but a binary-armf subdirectory within does not.
Your source URLs seem to be invalid.

See [https://askubuntu.com/questions/7058...apt-get-update]("https://askubuntu.com/questions/705895/how-to-fix-a-failed-to-fetch-binary-armhf-packages-error-during-apt-get-update") for two solutions.[/QUOTE]

The last solution was helping: sudo dpkg --remove-architecture armhf
This fixed it. I had before:
```
dpkg --print-foreign-architectures
i386
armhf

```

so now armhf is removed. Updating right now.
Thanks!

---

