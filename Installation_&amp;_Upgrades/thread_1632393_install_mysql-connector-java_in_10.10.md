---
title: "install mysql-connector-java in 10.10"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by andru183 on 2010-11-27
I have spent an entire day trying to install mysql-connector-java for either netbeans or eclipse and to no avail, I've followed all sorts of guides and copied the most up to date version of the file to usr/share/lib and changed the class path to it. I've added the .jar to both programs libaries, I still get 

```

Exception in thread "main" java.sql.SQLException: No suitable driver found for xxxxx

```


the issue stems from Class.forName("com.mysql.jdbc.Driver");

anyone of any help I will be so thankful for

---

### Post by andru183 on 2010-11-28
can anyone help?

---

### Post by lexqt on 2010-12-03
sudo apt-get install libmysql-java

---

