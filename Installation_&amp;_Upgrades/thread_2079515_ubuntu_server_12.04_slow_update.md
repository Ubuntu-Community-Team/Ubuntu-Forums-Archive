---
title: "ubuntu server 12.04 slow update"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by veesyndicate on 2012-11-01
hye guys. i want to ask,my update on ubuntu server are very slow. it is around 2++B/s only. why did this happen? i run a command apt-get update and my ubuntu server is set on vmware vsphere. So it is virtual. Do this problem occur because of limited available resources from ubuntu? or because it is virtual? thanks

---

### Post by ibjsb4 on 2012-11-01
Try a different mirror

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by veesyndicate on 2012-11-04
> **ibjsb4 said:**
> Try a different mirror

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)


Thanks for your suggestion dude. I just edit my update source list, and put the nearest and up-to-date server into the list. Very fast updating. Just want to ask, do i need to comment all existent list in source list so it just update using the new list i just edited? Because when i put the new list on top without comment current list, it will update using the source server i added, then later it will go to next server which is from ubuntu archieve. I really hate it because it is very slow. It is safe to comment? Thank you

---

