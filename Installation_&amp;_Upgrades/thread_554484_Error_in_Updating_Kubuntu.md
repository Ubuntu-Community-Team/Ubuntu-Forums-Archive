---
title: "Error in Updating Kubuntu"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by alirezza on 2007-09-19
Hi Every one

After I write the **apt-get update** command , it gets the following error :
some about my net connection :I use LAN and proxy server with authorization in my network , with net speed about 20 mb/s.
I can browse the net via browser , I set the proxy server in proxy tab in Network Setting in System Setting but i cant set the "use the following login information" in authorization tab in proxy tab , its disabled. but despite of this fact , I still can browse the net and while opening browser for the first time , it ask for my user/pass.

I also tried http://[user][:pass]@proxy:port/ for my proxy setting but still not work.

does any one have any idea ?

result after command :
```
root@alireza-laptop:/home/alireza# apt-get update
Ign http://us.archive.ubuntu.com feisty Release.gpg
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty-security Release.gpg
Ign http://us.archive.ubuntu.com feisty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates Release.gpg
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty Release
Ign http://us.archive.ubuntu.com feisty-security Release
Ign http://us.archive.ubuntu.com feisty-updates Release
Ign http://us.archive.ubuntu.com feisty/main Packages
Ign http://us.archive.ubuntu.com feisty/restricted Packages
Ign http://us.archive.ubuntu.com feisty/main Sources
Ign http://us.archive.ubuntu.com feisty/restricted Sources
Ign http://us.archive.ubuntu.com feisty/universe Packages
Ign http://us.archive.ubuntu.com feisty/universe Sources
Ign http://us.archive.ubuntu.com feisty/multiverse Packages
Ign http://us.archive.ubuntu.com feisty/multiverse Sources
Ign http://us.archive.ubuntu.com feisty-security/main Packages
Ign http://us.archive.ubuntu.com feisty-security/restricted Packages
Ign http://us.archive.ubuntu.com feisty-security/main Sources
Ign http://us.archive.ubuntu.com feisty-security/restricted Sources
Ign http://us.archive.ubuntu.com feisty-security/universe Packages
Ign http://us.archive.ubuntu.com feisty-security/universe Sources
Ign http://us.archive.ubuntu.com feisty-security/multiverse Packages
Ign http://us.archive.ubuntu.com feisty-security/multiverse Sources
Ign http://us.archive.ubuntu.com feisty-updates/restricted Packages
Ign http://us.archive.ubuntu.com feisty-updates/main Packages
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Packages
Ign http://us.archive.ubuntu.com feisty-updates/universe Packages
Err http://us.archive.ubuntu.com feisty/main Packages
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty/restricted Packages
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty/main Sources
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty/restricted Sources
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty/universe Packages
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty/universe Sources
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty/multiverse Packages
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty/multiverse Sources
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty-security/main Packages
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty-security/restricted Packages
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty-security/main Sources
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty-security/restricted Sources
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty-security/universe Packages
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty-security/universe Sources
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty-security/multiverse Packages
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty-security/multiverse Sources
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty-updates/restricted Packages
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty-updates/main Packages
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty-updates/multiverse Packages
  403 Forbidden [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com feisty-updates/universe Packages
  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz  403 Forbidden [IP: 91.189.89.8 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

thanks for your helping.

---

### Post by alirezza on 2007-09-19
Hi every one
It got solved with setting 
```
http_proxy="myproxydetails"
```
and 
```
export http_proxy
```
I have another question
how can i set the proxy user/pass in system setting > network setting > proxy > authorization ???
its disabled in my kubuntu
tnx.

---

