---
title: "Problem of Installing Apache2 With PHP5 And MySQL Support On Ubuntu 12.04 LTS (LAMP)"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by vinfospot on 2013-02-04
I've tried to install Lamp or Localhost server on ubuntu 12.04 LTS from [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-12.04-lts-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-12.04-lts-lamp)

The below code must open a new document file with gEdit/Test editor
```
vi /var/www/info.php
```

But with this command opened a new document file on Terminal on my pc. Why don't it open with geditor/text editor??

I need to open it on gEditor to to complete the installation of Lamp.

Please help me about it :( :(

---

### Post by Cheesemill on 2013-02-04
You've told your machine to open a file with vi and you're wondering why it doesn't open with gedit?

Try doing...
```
gedit /var/www/info.php
```

In fact you'll need root permissions to edit that file so the actual command you need would be...
```
gksudo gedit /var/www/info.php
```

---

### Post by vinfospot on 2013-02-05
> **Cheesemill said:**
> You've told your machine to open a file with vi and you're wondering why it doesn't open with gedit?

Try doing...
```
gedit /var/www/info.php
```

In fact you'll need root permissions to edit that file so the actual command you need would be...
```
gksudo gedit /var/www/info.php
```



Thank You very much :-) It works :KS

I'm a beginner in Ubuntu.. Can you suggest me a tutorial web blog from where i can learn most of the commands with explanation?

---

### Post by Cheesemill on 2013-02-05
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by vinfospot on 2013-02-05
> **Cheesemill said:**
> [https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)



Thanks :)

---

