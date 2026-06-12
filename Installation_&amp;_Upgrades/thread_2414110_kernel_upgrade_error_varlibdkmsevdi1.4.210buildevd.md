---
title: "kernel upgrade error /var/lib/dkms/evdi/1.4.210/build/evdi_connector.c"
date: 2019-03-06
forum: Installation &amp; Upgrades
---

### Post by dwater on 2019-03-06
Did a `sudo apt update` followed by a `sudo apt upgrade`, on Ubuntu 18.04.2 LTS.

It seems to be attempting to install linux-image-4.15.0-46-generic:

```
Processing triggers for linux-image-4.15.0-46-generic (4.15.0-46.49) ...
/etc/kernel/postinst.d/dkms:
ERROR (dkms apport): binary package for evdi: 1.4.210 not found
Error! Bad return status for module build on kernel: 4.15.0-46-generic (x86_64)
Consult /var/lib/dkms/evdi/1.4.210/build/make.log for more information.

```

 There are some warnings, but this is the error:

```

/var/lib/dkms/evdi/1.4.210/build/evdi_connector.c:90:6: error: too few arguments to function ‘drm_mode_object_find’
      drm_mode_object_find(connector->dev, enc_id,
      ^~~~~~~~~~~~~~~~~~~~
In file included from ./include/drm/drm_crtc.h:38:0,
                 from ./include/drm/drmP.h:69,
                 from /var/lib/dkms/evdi/1.4.210/build/evdi_connector.c:13:
./include/drm/drm_mode_object.h:117:25: note: declared here
 struct drm_mode_object *drm_mode_object_find(struct drm_device *dev,
                         ^~~~~~~~~~~~~~~~~~~~
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/evdi/1.4.210/build/evdi_connector.o' failed
make[2]: *** [/var/lib/dkms/evdi/1.4.210/build/evdi_connector.o] Error 1

```

I wonder how to 'try again', since the packages were actually installed successfully.

---

