---
title: "problem with flash player plugin in ubuntu 9.10"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by skkmaths on 2010-01-22
i have problem with installinf flashplugin in ubuntu 9.10. i tried it through synaptic package manager , there it shows connecting to archive,canonical.com and it will  not proceed after that ,,,,please help me to resolve this problem ..please mail me to [email]skkmaths@gmail.com[/email]

---

### Post by n0dix on 2010-01-22
Try to run:
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by skkmaths on 2010-01-22
i run the first command and i got the following thing,,,and itis not moving further it stands still in 0%


Writing extended state information... Done
0% [Connecting to archive.ubuntu.com (91.189.88.45)] [Connecting to archive.canoniErr [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg             
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
0% [Connecting to archive.ubuntu.com (91.189.88.46)] [Connecting to download.skype.com (78.141.179.3)]

---

### Post by n0dix on 2010-01-22
Then make sure that in network proxy you have direct connection. 
and use sudo apt-get update. 
that should work.

---

### Post by skkmaths on 2010-01-22
But  i am using  a proxy server connection ..please help me .....

---

### Post by n0dix on 2010-01-22
You can set proxy settings manually for the shell you're in and you could place the same lines into e.g. ~/.bashrc so that these commands are auto-executed whenever you open a shell. The commands:
export http_proxy=http://your.proxy.server.here:12345/
export ftp_proxy=http://your.proxy.server.here:12345/

---

### Post by skkmaths on 2010-01-23
i did not under stand what you said ,i use http proxy in reprosities >network>,,,,and  i can  download all other packeage with  out any problem 

please help me

---

### Post by skkmaths on 2010-01-26
please help me i am still not able to do it

---

