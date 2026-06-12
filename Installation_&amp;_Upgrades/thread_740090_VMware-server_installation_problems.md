---
title: "VMware-server installation problems"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by robertchahine on 2008-03-30
i've installed vmware-server and when i wirte
```
vmware
```
in the terminal i get this error
```
/usr/bin/vmware: 166: cannot open /etc/vmware/locations: No such file
exec: 180: /lib/wrapper-gtk24.sh: not found

```

i tried this 
```
 sudo apt-get -f install

```

and this is the output
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up vmware-server (1.0.4-1gutsy2) ...
/etc/init.d/vmware-server: 176: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-server, action "start" failed.
dpkg: error processing vmware-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

how to fix this?

---

### Post by upthelum on 2008-03-30
Try dpkg --configure

---

### Post by robertchahine on 2008-03-31
> **upthelum said:**
> Try dpkg --configure

i tried it and still have the same error

---

