---
title: "PHP mysqli broken after distro upgrade to Xubuntu 19-10"
date: 2020-03-31
forum: Installation &amp; Upgrades
---

### Post by ndb2 on 2020-03-31
So far, certain (old and maintained) code worked fine. However... not any more. PHP says...
> "Call to undefined function mysqli_connect()"

I'm using nginx with supervisor to run a local PHP CGI service within a box for dev purposes (nowadays mostly HTML and Node.js).

According to php info, mysqli and mysqlnd are installed and operational.
Checked which php.ini file is loaded.

Output from package manager about installed PHP packages:
```

i   php-mysql             
v   php-mysqli            
v   php-mysqli:i386       
v   php-mysqlnd           
v   php-mysqlnd:i386      
v   php-pdo-mysql         
v   php-pdo-mysql:i386    
i   php7.2-mysql          
v   php7.2-mysqli         
v   php7.2-mysqlnd        
v   php7.2-pdo-mysql      
i A php7.3-mysql          
p   php7.3-mysql:i386     
v   php7.3-mysqli         
v   php7.3-mysqli:i386    
v   php7.3-mysqlnd        
v   php7.3-mysqlnd:i386   
v   php7.3-pdo-mysql      
v   php7.3-pdo-mysql:i386 

```

The only thing noticeble for myself are virtual packages of two PHP versions.

Any ideas how to solve this issue?

---

### Post by ndb2 on 2020-04-06
Solved by complete reinstall of PHP

---

