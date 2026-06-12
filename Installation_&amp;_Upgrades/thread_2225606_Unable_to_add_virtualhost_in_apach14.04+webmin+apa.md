---
title: "Unable to add virtualhost in apach14.04+webmin+apache"
date: 2014-05-22
forum: Installation &amp; Upgrades
---

### Post by gopukrishnan on 2014-05-22
Hi all,

  I am not able to create any virtual srevers in fresh webmin + apache  installation. Getting the below errors when I try to add a domain :
  Failed to create virtual server : The new virtual server was added to  /etc/apache2/sites-available/****.com.conf, but this file is not used  by Apache. Check the module configuration and make sure the 'File or  directory to add virtual servers to' is correct.
  Following are enabled in apache2.conf:
    IncludeOptional conf-enabled/*.conf
    IncludeOptional sites-enabled/*.conf


  I have tried to install the apache from webmin but the issue  persists. I have attached the errors and current configurations. Please  check and assist.

[http://postimg.org/image/9chiyb2bh/](http://postimg.org/image/9chiyb2bh/)
[http://postimg.org/image/4vp5zmo3h/](http://postimg.org/image/4vp5zmo3h/)
[http://postimg.org/image/6jobea1z1/](http://postimg.org/image/6jobea1z1/)
[http://postimg.org/image/wx37dbtdp/](http://postimg.org/image/wx37dbtdp/)
[http://postimg.org/image/qko23hqbh/](http://postimg.org/image/qko23hqbh/)
[http://postimg.org/image/x7apwo7zx/](http://postimg.org/image/x7apwo7zx/)

---

