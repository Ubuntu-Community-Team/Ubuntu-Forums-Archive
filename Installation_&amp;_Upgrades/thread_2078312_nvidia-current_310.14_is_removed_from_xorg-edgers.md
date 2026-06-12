---
title: "nvidia-current 310.14 is removed from xorg-edgers ?"
date: 2012-10-30
forum: Installation &amp; Upgrades
---

### Post by funicorn on 2012-10-30
That's wired. I can not see the package name using 
```

apt-cache madison nvidia-current

```> 
nvidia-current | 304.51.really.304.43-0ubuntu1 | [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) quantal/restricted amd64 Packages
nvidia-current | 304.51.really.304.43-0ubuntu1 | [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/restricted amd64 Packages
nvidia-graphics-drivers | 304.51.really.304.43-0ubuntu1 | [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) quantal/restricted Sources
nvidia-graphics-drivers | 304.51.really.304.43-0ubuntu1 | [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/restricted Sources
And
```

dpkg -l nvidia-current

```> 
ii  nvidia-current             310.14-0ubuntu1~xe amd64              NVIDIA binary Xorg driver, kernel module and VDPAU library


What are they doing ?

---

