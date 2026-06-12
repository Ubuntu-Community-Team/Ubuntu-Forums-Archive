---
title: "gstreamer0.10-plugins-farsight installation failed problem for pidgin package install"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by mortasa on 2010-08-26
Hello!

I'm using Ubuntu jaunty and was using old version of pidgin until today. Today I had decided to install newer version of Pidgin 2.7 and uninstalled my old version from system. Because it had so many problem like not login to yahoo account.

I went to Pidgin website and downloaded Debian package for ubuntu. But got an error while installing. Finally I decided to install it from source package and downloaded it to install. 

While I try to make configure file by typing ```
./configure
``` command, it gave me following error:

```
checking for update_panels in -lpanel... no
checking for LIBXML... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for GSTREAMER... yes
checking for gst_registry_fork_set_enabled in -lgstreamer-0.10... yes
checking for GSTINTERFACES... yes
checking for FARSIGHT... no
configure: error: 
Dependencies for voice/video were not met.
Install the necessary gstreamer and farsight packages first.
Or use --disable-vv if you do not need voice/video support.

```

So I installed all available gstreamer packages via synaptic package manager. But when I try to install gstreamer0.10-plugins-farsight, I got following error:

```
E: /var/cache/apt/archives/gstreamer0.10-plugins-farsight_0.12.10-2_i386.deb: trying to overwrite `/usr/lib/gstreamer-0.10/libgstdtmf.so', which is also in package gstreamer0.10-plugins-good
```

So I can not install Pidgin now. If I have to install it anyway I have to disable video and voice service for Pidgin. But I would like to use Pidgin with video and voice. Anybody can recommend a good solution for me please..

Regards,
Mort.

---

### Post by mortasa on 2010-08-28
Finally Upgraded to Lucid. Nothing more to feel worry now. But still it was a problem for me.

Thanks.
Mort,:popcorn:

---

### Post by limotux on 2011-01-14
BUMP!

I'm on Lucid, trying to install amsn with voice as shown at [http://www.amsn-project.net/wiki/Farsight](http://www.amsn-project.net/wiki/Farsight)

but still getting ```
E: Unable to find a source package for gstreamer0.10-plugins-farsight
```

Any help highly appreciated.

---

### Post by limotux on 2011-01-14
well... it's ok... I read somwhere that voice will not work because M$ changed things... so now amsn will not work with voice.

---

