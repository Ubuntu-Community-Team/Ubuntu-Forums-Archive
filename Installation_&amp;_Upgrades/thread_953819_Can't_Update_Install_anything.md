---
title: "Can't Update/ Install anything"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by Oh_Buhnanerz on 2008-10-20
No matter what I try to install using the add/ remove applications or how I try to update (any package manager) I have this same error message: 

"failed in buffer_read(fd)"

I am fairly new to Ubuntu but have always figured how to fix things but this has me stumped.:confused::mad:](*,)

Thanks in advance :p

Eddit:
I tried the following suggested by Jouke74
```
Open up a terminal and try the following commands first:
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoclean
```

and during the upgrade I received this message:
```
(Reading database ... dpkg: error processing /var/cache/apt/archives/linux-libc-dev_2.6.24-21.42_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `sun-java6-jre': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/linux-libc-dev_2.6.24-21.42_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

makes me want to wipe my HDD:mad:

---

### Post by Partyboi2 on 2008-10-21
Maybe you can try rengerating the sun-java6-jre.list file. Open a terminal and check that you have sun-java6-jre_6-06-0ubuntu1_all.deb (assuming you are using hardy) in /var/cache/apt/archives.
```
cd /var/cache/apt/archives
``````
ls sun-java6-jre*
``` if it says>  ls: cannot access sun-java6-jre*: No such file or directorymeans that you will need to go [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/hardy/all/sun-java6-jre/download") and download it and move it to /var/cache/apt/archives.
```
sudo mv /home/*/Desktop/sun-java6-jre_6-06-0ubuntu1_all.deb /var/cache/apt/archives
``` then once sun-java6-jre_6-06-0ubuntu1_all.deb is in the /var/cache/apt/archives 
give this terminal session admin rights
```
sudo -s
```then
```
dpkg -c /var/cache/apt/archives/sun-java6-jre_6-06-0ubuntu1_all.deb > /var/lib/dpkg/info/sun-java6-jre.list
```then
```
apt-get -f install
apt-get update
apt-get upgrade
```

---

