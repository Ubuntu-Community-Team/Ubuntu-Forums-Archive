---
title: "apt-get install vsftpd - how do I change the config file directory"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by HiTiredImJ on 2010-06-14
Is there a way to change the config file directory for vsftpd (or anything else installed with apt-get)? Right now, the file vsftpd.conf is dropped naked into /etc/ and I'd rather put it inside of a container, since I have the user_list and other files that aren't explicitly labeled as belonging to vsftp.

My installation was done with a simple apt-get statement.

$ sudo apt-get install vsftpd

on Ubuntu 8.04 LTS

I've dug through the forums and done my usual google-fu, but I haven't found anything on the subject. Could someone point me in the right direction?

---

