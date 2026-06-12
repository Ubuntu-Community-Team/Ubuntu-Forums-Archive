---
title: "Unable to Install, Remove And Upgrade"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by Aneesh John on 2010-06-02
After installing google Chrome web browser, I am unable to do any installation, upgrade and removal. Whenever trying to Install or remove any program the below message is provided.
"Removing libvpx0 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libvpx0 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 libvpx0
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Please find the details of **"libvpx0"**

VP8 is an open video codec, originally developed by On2 and released
as open source by Google Inc. It is the successor of the VP3 codec,
on which the Theora codec was based.
This package contains the shared libraries.

Expecting a solution.

---

### Post by lemming465 on 2010-06-04
If *dpkg --remove libvpx0* doesn't get rid of it, you could maybe try *dpkg --remove --force-remove-reinstreq*.  Or *aptitude update; aptitude reinstall libvpx0*.  I'm not sure if these will fix it or not.

---

