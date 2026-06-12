---
title: "Failed to install firefox mobile os b2g in ubuntu13.04"
date: 2013-09-03
forum: Installation &amp; Upgrades
---

### Post by hema2 on 2013-09-03
Hi,
I am  trying to install firefox mobile os b2g on ubuntu . I have downloaded and installed gaia. But when I am trying to run firefoxmobile b2g I am getting errors. Can anyone please help  me in finding where I am going wrong. Below are the steps I am following:
1. Downloaded  [b2g-26.0a1.multi.linux-i686.tar.bz2]("http://ftp.mozilla.org/pub/mozilla.org/b2g/nightly/latest-mozilla-central/b2g-26.0a1.multi.linux-i686.tar.bz2") from [http://ftp.mozilla.org/pub/mozilla.org/b2g/nightly/latest-mozilla-central/](http://ftp.mozilla.org/pub/mozilla.org/b2g/nightly/latest-mozilla-central/)
2. Extracted it in Downloads folder only.
3. From terminal I have downloaded and installed gaia using the command
                   git clone [http://github.com/mozilla-b2g/gaia](http://github.com/mozilla-b2g/gaia) 
     then        make -C gaia profile
4.  When the profile is ready I tried to run firefox mobile b2g 
                   testlab2@testlab2-HP-Compaq-Elite-8300-SFF:~/Downloads/b2g$ cd b2g
                   [COLOR=#ff0000]bash: cd: b2g: Not a directory[/COLOR]
  I tried this one also 
                  testlab2@testlab2-HP-Compaq-Elite-8300-SFF:~/Downloads/b2g$ -profile /home/testlab2/Downloads/b2g/gaia
                [COLOR=#ff0000] -profile: command not found

[/COLOR]By the by here are my Ubuntu specifications:
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring
kernel version: 3.8.0-29-generic
kernel information: Linux testlab2-HP-Compaq-Elite-8300-SFF 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Can anyone please help me out to solve this problem.
Thanks in advance

---

