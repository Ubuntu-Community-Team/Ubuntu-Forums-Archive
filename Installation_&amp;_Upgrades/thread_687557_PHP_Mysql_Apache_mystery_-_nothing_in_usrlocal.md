---
title: "PHP Mysql Apache mystery - nothing in /usr/local"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by dieselpop on 2008-02-04
I am utterly befuddled.

Have just installed PHP, Apache & Mysql through the package manager

An empty database is setup and  a web page is displaying through the server.

Thing is, the manuals for these applications all state that several files are located in /usr/local but on my machine there are only the following.

bin  
etc  
games 
include  
lib  
man  
sbin  
share  
src

Am I being a total doofus? Whats up?

---

### Post by dieselpop on 2008-02-04
Answered my own question. 

All the configuration files are in /etc

```

ls /etc | grep "php\|apache\|mysql"
apache2
mysql
php5

```

I am a doofus, but why should the configuration in Ubuntu be different from whats stated in the manuals.

---

