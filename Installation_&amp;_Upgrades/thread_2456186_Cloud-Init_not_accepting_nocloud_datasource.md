---
title: "Cloud-Init not accepting nocloud datasource"
date: 2021-01-06
forum: Installation &amp; Upgrades
---

### Post by scahartner on 2021-01-06
I am trying to boot a bare-metal system running ubuntu 20 and use cloud-init with the nocloud datasource ([https://cloudinit.readthedocs.io/en/latest/topics/datasources/nocloud.html](https://cloudinit.readthedocs.io/en/latest/topics/datasources/nocloud.html)) to apply the initial configuration.

I was thinking about updating grub to apply the settings:

```
ds=nocloud-net;s=http://10.10.0.1:8000/
```

 and then host the user-data and meta-data files via http.

However I am not sure were I need to specify the grub parameters.

```
root@ubuntu-base:/home/user# cloud-init status --long
status: done
time: Wed, 06 Jan 2021 09:53:14 +0000
detail:
DataSourceNone

```

The system was installed using PXE and autoinstall so cloud-init has already been installed and seems to be working. I am hoping that I just have to introduce a new datasource and then apply the configration via user-data.

Any pointers on how to pass these parameters to the system.

---

### Post by scahartner on 2021-01-07
Tried updating /etc/default/grub with the following

```
GRUB_DEFAULT=0
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=30
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="serial=ds=nocloud-net;seedfrom=http://192.168.0.172/ubuntu/config/"
GRUB_CMDLINE_LINUX="serial=ds=nocloud-net;seedfrom=http://192.168.0.172/ubuntu/config/"

```

However this doesn't work. I don't see any request on the http server side and cloud-init still reports no data source.

---

### Post by scahartner on 2021-01-07
Even using this did not work either:
```
GRUB_DEFAULT=0
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="-smbios type=1,serial=ds=nocloud-net\;seedfrom=http://192.168.0.172/ubuntu/config/ ds=nocloud-net\;seedfrom=http://192.168.0.172/ubuntu/config/"
GRUB_CMDLINE_LINUX="-smbios type=1,serial=ds=nocloud-net\;seedfrom=http://192.168.0.172/ubuntu/config/ ds=nocloud-net\;seedfrom=http://192.168.0.172/ubuntu/config/"

```

---

