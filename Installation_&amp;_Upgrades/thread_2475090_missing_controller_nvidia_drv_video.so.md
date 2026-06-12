---
title: "missing controller: nvidia_drv_video.so"
date: 2022-05-16
forum: Installation &amp; Upgrades
---

### Post by enrialba on 2022-05-16
Hello!
I installed ubuntu 22.04, but some applications that use "electron" fail to start when I use the proprietary drivers of my nvidia graphics card (no problem with intel integrated graphics):
```

libva error: vaGetDriverNameByIndex() failed with unknown libva error, driver_name = (null)
libva error: vaGetDriverNameByIndex() failed with unknown libva error, driver_name = (null)
libva error: vaGetDriverNameByIndex() failed with unknown libva error, driver_name = (null)
[2245:0516/151734.344212:FATAL:gpu_data_manager_impl_private.cc(415)] GPU process isn't usable. Goodbye.

```

The "vainfo" utility gives me this error:
```

libva info: VA-API version 1.14.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/nvidia_drv_video.so
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```


Thank you very much for the help!

---

