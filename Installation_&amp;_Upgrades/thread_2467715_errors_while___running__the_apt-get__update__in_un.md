---
title: "errors while   running  the apt-get  update  in unbuntu20"
date: 2021-10-06
forum: Installation &amp; Upgrades
---

### Post by ncgjiju138 on 2021-10-06
Hi  ,


i  am   patching   ubuntu 20

 in  the server i have  downloading the repo  for 20 and i have also downloaded the  repo an cnf also.

In the client  when i run  apt-get  update  ,  

Now  i getting error while   i do apt-get  update -
file has unexpected size (8824 !=8712)  mirror sync in progress  ? [ip:xxx.xxx.xxx.xx 80]
hashes of expected filw:
-Filesize 8712  [Weak]
-SHA256:DDDDDD
-SHA1:02XXXXXXXXXXX [Weak]
-Md5Sum:1f  dddd [weak]
release file created on on 17th  Sept 2021


regards,


Christy

---

### Post by MAFoElffen on 2021-10-06
> 
file has unexpected size (8824 !=8712)  [COLOR=#ff0000]mirror sync in progress[/COLOR]  ? [ip:mad:xx.xxx.xxx.xx 80]
hashes of expected filw:
-Filesize 8712  [Weak]
-SHA256:grin:DDDDD
-SHA1:02XXXXXXXXXXX [Weak]
-Md5Sum:1f  dddd [weak]
release file created on on 17th  Sept 2021

Is this is this an external repo or mirror, or local repo you created on your local network infrastructure? If local, did you just download, or use one of the local repo packages that keeps the local repo's synced, such as "apt-mirror"? If the later, then check your logs and see if it was doing a sync when you hit it.

---

