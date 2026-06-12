---
title: "Can't install upgrades"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by tornadoes28 on 2011-12-18
I am connected via wifi with no problem. But I am not able to install updates. I keep getting error message saying I need to check connection. Error window includes the following error message below.


Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-3.0.0-14-generic_3.0.0-14.23_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-3.0.0-14-generic_3.0.0-14.23_i386.deb) 404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/at-spi2-core/libatspi2.0-0_2.2.2-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/at-spi2-core/libatspi2.0-0_2.2.2-0ubuntu1_i386.deb) 404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/at-spi2-core/at-spi2-core_2.2.2-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/at-spi2-core/at-spi2-core_2.2.2-0ubuntu1_i386.deb) 404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9-common_9.04~dfsg-0ubuntu11.2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9-common_9.04~dfsg-0ubuntu11.2_all.deb) 404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_9.04~dfsg-0ubuntu11.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_9.04~dfsg-0ubuntu11.2_i386.deb) 404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_9.04~dfsg-0ubuntu11.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_9.04~dfsg-0ubuntu11.2_i386.deb) 404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9_9.04~dfsg-0ubuntu11.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9_9.04~dfsg-0ubuntu11.2_i386.deb) 404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-cups_9.04~dfsg-0ubuntu11.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-cups_9.04~dfsg-0ubuntu11.2_i386.deb) 404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/at-spi2-core/gir1.2-atspi-2.0_2.2.2-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/at-spi2-core/gir1.2-atspi-2.0_2.2.2-0ubuntu1_i386.deb) 404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-headers-3.0.0-14_3.0.0-14.23_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-headers-3.0.0-14_3.0.0-14.23_all.deb) 404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-headers-3.0.0-14-generic_3.0.0-14.23_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-headers-3.0.0-14-generic_3.0.0-14.23_i386.deb) 404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-globalmenu_7.0.1+build1+nobinonly-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-globalmenu_7.0.1+build1+nobinonly-0ubuntu2_i386.deb) 404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_7.0.1+build1+nobinonly-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_7.0.1+build1+nobinonly-0ubuntu2_i386.deb) 404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-gnome-support_7.0.1+build1+nobinonly-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-gnome-support_7.0.1+build1+nobinonly-0ubuntu2_i386.deb) 404  Not Found [IP: 91.189.88.31 80]

---

### Post by 2F4U on 2011-12-18
I looked at the first entry which it complains about:

[http://archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-3.0.0-14-generic_3.0.0-14.23_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-3.0.0-14-generic_3.0.0-14.23_i386.deb)

This is a version of the kernel that is no longer available on the server, since the current version is 

[http://archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-3.0.0-15-generic_3.0.0-15.24_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-3.0.0-15-generic_3.0.0-15.24_i386.deb)

Did you refresh your repositories?

sudo apt-get update

---

### Post by tornadoes28 on 2011-12-18
Thank you. Fixed.

---

