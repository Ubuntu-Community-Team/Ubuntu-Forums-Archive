---
title: "Gue of Install apache mysql and php"
date: 2016-11-10
forum: Installation &amp; Upgrades
---

### Post by willian.bumba on 2016-11-10
I am trying to install apache, mysql and php 
using $ sudo apt install apche2; this command is not installing full apache server. please give me a tutorial.
Ubuntu 16.04.1.

---

### Post by SeijiSensei on 2016-11-10
It always helps to read the existing documentation: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Run the commands
```

sudo apt-get update
sudo apt-get install lamp-server^
```
and everything you need will be installed.  Make sure to include the caret ("^") on the end.

---

