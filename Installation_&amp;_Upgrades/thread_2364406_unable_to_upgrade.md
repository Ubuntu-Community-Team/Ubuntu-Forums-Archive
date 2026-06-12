---
title: "unable to upgrade"
date: 2017-06-22
forum: Installation &amp; Upgrades
---

### Post by davidmadsen on 2017-06-22
Hi all! I have had a number of problems with Ubuntu lately, however it comes done to the same error message all the time which i think is due to some update I'm unable to do.... when running sudo apt-get upgrade i get the error message:  ```
dpkg: error processing package linux-signed-generic (--configure):  dependency problems - leaving unconfigured Errors were encountered while processing:   linux-image-4.4.0-81-generic   linux-image-extra-4.4.0-81-generic   linux-image-generic   linux-generic   linux-signed-image-4.4.0-81-generic   linux-signed-image-generic   linux-signed-generic  E: Sub-process /usr/bin/dpkg returned an error code (1)
```    I would really appreciate all the help i can get! Cheers!

---

### Post by deadflowr on 2017-06-22
Try
```
sudo apt-get update && sudo apt-get dist-upgrade
```
if still erring out, then try
```
sudo apt-get install -f
```
post results if problems still occur.

---

