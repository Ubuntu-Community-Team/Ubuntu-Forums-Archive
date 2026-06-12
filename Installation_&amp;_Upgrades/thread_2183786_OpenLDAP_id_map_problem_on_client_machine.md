---
title: "OpenLDAP id map problem on client machine"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by webappl on 2013-10-26
I have installed OpenLDAP and shared the ldap user home directory through NFS. On a OpenLDAP client machine, running 'id' command returns the correct user id and group information for a ldap user. However, using 'ls -l' to check the details of ldap user's files failed to map to the correct id and group. Eg, I got nobody and nogroup for a txt file

       -rw-r--r-- 1 nobody nogroup    4 Oct 26 14:58 test.txt

How to solve this id mapping problem here?

Thanks,

Alex

---

### Post by webappl on 2013-10-26
I found a solution
[http://serverfault.com/questions/364613/centos-6-ldap-nfs-file-ownership-is-stuck-on-nobody](http://serverfault.com/questions/364613/centos-6-ldap-nfs-file-ownership-is-stuck-on-nobody)

Edit file /etc/idmapd.conf on the client by setting the option Domain with the domain name of the server, such as
Domain = example.com

Restart idmapd service and then re-mount the nfs shared folder
sudo service idmapd restart
sudo umount /shared/directory
sudo mount /shared/directory

---

