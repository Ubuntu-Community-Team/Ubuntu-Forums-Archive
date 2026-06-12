---
title: "W3C-Validator install problems"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by vuetrip on 2011-08-21
installed the W3C-Validator from the Software Centre after installing the missing dependency fron oneric.

But now I get a 403 when visiting [http://localhost/cgi-bin/w3c-markup-validator/](http://localhost/cgi-bin/w3c-markup-validator/)

Think this is most likely a file permissions issue but am not sure which file/directory to chown?

---

### Post by fdrake on 2011-08-21
> **vuetrip said:**
> installed the W3C-Validator from the Software Centre after installing the missing dependency fron oneric.
 
But now I get a 403 when visiting [http://localhost/cgi-bin/w3c-markup-validator/](http://localhost/cgi-bin/w3c-markup-validator/)

Think this is most likely a file permissions issue but am not sure which file/directory to chown?

it looks like your webserver does not have execution or write/read permission of that file/folder. do
```

less /etc/passwd | grep /var/www | cut -d ":" -f 1

```
(usually is somthinng like "www-data")
this will output the <name> of your webserver
then do
```

sudo chown -R <name> /var/www/*

```
this will make all the files/folders in www owned by the server-user.

note: if you want your username and server bot to be able to edit/ write execute the files just add bot the servername and your username to a common group. than do 
```

sudo cgrp -R <group_name> /var/www/* 

```

---

