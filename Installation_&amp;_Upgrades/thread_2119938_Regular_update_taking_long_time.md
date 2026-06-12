---
title: "Regular update taking long time"
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by EthioJOB on 2013-02-25
I use Ubuntu 12.04 on Toshiba C650.

Lately whenever I install updates it has been taking a little time to finish, especially when it reaches this line of text:

*flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.orig.tar.gz)*

Recently it has been taking a noticeably long time. I don't want it to cause future problems. Right now as I write it hasn't been moving for a long time and I'm afraid to shut it down. Why is this so? What can I do to make it stop drag on like this?

---

### Post by ali abry on 2013-02-25
it can be slow Internet connection cause so much time to files being download .
you can use this command to get url of files and import them to a download manager that can download with higher speed . 
```
 $ sudo apt-get upgrade --yes --print-uris | grep http |cut -d " " -f 1 | tr -d \'
```
after downloading move them to var/cache/apt/archive and run this command 
sudo apt-get update

---

### Post by EthioJOB on 2013-02-25
Actually the internet is just fine. It always start to get stuck whenever it reaches the line I mentioned. This process is when after the files are downloaded and during the installation/update process.

---

### Post by EthioJOB on 2013-02-25
Just wanted to say that I it worked. Also, the command and tip you gave is one I like very much and can come in handy.

Thank you.

---

