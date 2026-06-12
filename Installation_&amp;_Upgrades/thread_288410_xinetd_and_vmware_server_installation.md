---
title: "xinetd and vmware server installation"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by zog on 2006-10-29
Hi All,

I am having real difficulty tyring to get vmware server installed on my ubuntu 6.10 server installation. I run through the entire installation and at the very end I get the following error:

unable to set the last modification timestamp to the destination file:
/etc/vmware/ssl/rui.key

When I look in the xinetd log I see the following entry:

ERROR: 9159 bind failed (Address already in use).

I'm not familiar with xinetd at all and needed help just getting that installed. Does anyone have any insight into what might be the issue. 

All help appreciated.

---

### Post by mentok on 2006-11-10
I have the same problem. I just installed Kubuntu Edgy AMD64 and have been trying to install VMware-server-1.0.1-29996.

I got the same error you've been having so I did
```
sudo touch /etc/vmware/ssl/key.rui
sudo touch /etc/vmware/ssl/key.crt
```

And it seemed to work until I got to entering the license key:

```
sh: /usr/lib/vmware/bin/vmware-vmx: not found
The serial number 12345-12345-12345-12345 is invalid.
```

I guess that it uses the 'vmware-vmx' program to check the serial number cause my serial used to work on Dapper.

Also, when probing for unused subnets, earlier in the process, it couldn't find the 'vmware-ping' program so I had to enter the subnets manually.

Something is definitely broken somewhere. :mad:

---

### Post by mentok on 2006-11-10
I installed 'ia32-libs' as suggested in this thread:

[http://www.ubuntuforums.org/showthread.php?t=291287]("http://www.ubuntuforums.org/showthread.php?t=291287")

and it works now! :mrgreen:

---

