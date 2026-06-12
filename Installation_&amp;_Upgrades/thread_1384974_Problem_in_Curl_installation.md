---
title: "Problem in Curl installation"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by ramakrishnankt on 2010-01-19
Hi,
I am installed cUrl from [http://packages.ubuntu.com/lucid/amd64/curl/download](http://packages.ubuntu.com/lucid/amd64/curl/download) for my ubuntu 9.0 with php 5.2 ,Apache 2.0.It was installed by gkebi  package installer. but when i display phpinfo() curl not found since i was attempt to use phptwitter class.
what is the proble i have?
When i am trying to install again package installer shows same version of curl already found, but phptwitterclass shows following error

'Method "curlQuery" of class "Twitter" reported an error:
CURL library not installed.'
Regards
Ramakrishnankt

---

### Post by ramakrishnankt on 2010-01-19
I got solution from curl-and-php mailing list
sudo apt-get install php5-curl
More help can be found here:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Thanks
Ramakrishnankt

---

