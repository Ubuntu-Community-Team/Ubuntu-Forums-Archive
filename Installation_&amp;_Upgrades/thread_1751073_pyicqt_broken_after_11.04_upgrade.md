---
title: "pyicqt broken after 11.04 upgrade"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by ulukay on 2011-05-06
since ubuntu decided to upgrade python-twisted to an incompatible version (10.2), pyicqt is not running any more. (bugreport is already open)

if you need a fast solution - download the following packages manually from the debian ftps (e.g. [http://ftp.at.debian.org/debian/pool/main/t/](http://ftp.at.debian.org/debian/pool/main/t/) ):
python-twisted_11.0.0-2_all.deb        
python-twisted-names_11.0.0-1_all.deb
python-twisted-bin_11.0.0-2_amd64.deb  
python-twisted-news_11.0.0-1_all.deb
python-twisted-conch_11.0.0-1_all.deb  
python-twisted-runner_11.0.0-1_amd64.deb
python-twisted-core_11.0.0-2_all.deb   
python-twisted-web_11.0.0-1_all.deb
python-twisted-lore_11.0.0-1_all.deb   
python-twisted-words_11.0.0-1_all.deb
python-twisted-mail_11.0.0-1_all.deb

and install them with dpkg

---

