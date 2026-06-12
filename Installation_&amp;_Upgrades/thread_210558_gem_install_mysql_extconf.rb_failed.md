---
title: "gem install mysql ***extconf.rb failed***"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by jmvbxx on 2006-07-07
I've installed rails (and it works) and now I want to be able to connect to a mysql database.

The database.yml file tells me to install the mysql drivers by typing:

gem install mysql

This is the error I receive:

[I]Could not create Makefile due to some reason, probably lack of
necessary libraries and/or headers.  Check the mkmf.log file for more
details.  You may need configuration options.[/I]

Any help is greatly appreciated!  Thank you!

---

### Post by XtremeBain on 2006-09-07
Hi there,

I was experiencing the same problems myself.  I looked at mkmf.log and realized that gems couldn't load the mysqlclient libraries, which led to the following solutions:

If you're using MySQL 5.0:
```
sudo apt-get install libmysqlclient15-dev
```

If you're using MySQL 4.x:
```
sudo apt-get install libmysqlclient12-dev
```

Hope this helps :)

---

