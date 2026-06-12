---
title: "Lucid-official-Issue when upgrading from Lucid Alpha 2"
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-02-26
"If you installed Lucid prior to  Alpha 3, you may have libmysqlclient16 7.0.9-1 installed.  This  package was present in the Ubuntu archive by mistake and was retracted,  but because it has a later version number than the real libmysqlclient16  package, the real package will not be installed automatically on  upgrade.  

To ensure that you have the official package installed on your  Lucid system and will receive security support for it throughout Ubuntu  10.04 LTS, please run ***sudo apt-get install libmysqlclient16/lucid***  and follow the instructions. " 

[http://www.ubuntu.com/testing/lucid/alpha3](http://www.ubuntu.com/testing/lucid/alpha3)
This should be "Sticky" IMHO.

---

