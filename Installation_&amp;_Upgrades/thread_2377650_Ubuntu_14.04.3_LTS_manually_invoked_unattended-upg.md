---
title: "Ubuntu 14.04.3 LTS manually invoked unattended-upgrade fails"
date: 2017-11-15
forum: Installation &amp; Upgrades
---

### Post by desdan on 2017-11-15
I am attempting to manually run the unattended-upgrade for security only updates. I am running 14.04.3 LTS server. I've checked the /etc/apt/apt.conf.d/50unattended-upgrades file to make sure it is set to upgrade only security updates.
When I run 'unattended-upgrade' at the command prompt it pauses (ostensibly because it is trying to download the upgrade), but it eventually reports[INDENT][I]
An error occurred: '404  Not Found [IP: 2001:67c:1360:8001::17 80]'[/I]
[I]The URI 'http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1f-1ubuntu2.22_amd64.deb' failed to download, aborting
[/I][/INDENT]
[I]
I checked out the URI [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/) and found that indeed there is no file by the name of
**libssl1.0.0_1.0.1f-1ubuntu2.22_amd64.deb**
but there is a file called **libssl1.0.0_1.0.1f-1ubuntu2.2[COLOR=#ff0000]3[/COLOR]_amd64.deb** (note the only change is in red)
[/I]
Assuming I can use the ...2.23_amd64.deb file, how do I tell my system to use that file?If I cannot use that file, where do I point the unattended-upgrade to get the missing file (and how do I set it)?
Thanks
[I]
Des
[/I]

---

### Post by deadflowr on 2017-11-15
You error out because the automatic unattended-upgrades settings run sudo apt-get update first, before attempting to invoke the unattended-upgrade command.
So you need to do that too.

---

### Post by desdan on 2017-11-15
Ah - that makes sense.  Thanks - worked as expected.

---

### Post by mörgæs on 2017-11-15
Good, please mark the thread solved.

---

