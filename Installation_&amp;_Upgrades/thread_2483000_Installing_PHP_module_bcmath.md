---
title: "Installing PHP module bcmath"
date: 2023-01-17
forum: Installation &amp; Upgrades
---

### Post by asai on 2023-01-17
Hi,

I have som trouble installing the bcmath module on my Ubuntu server.

Installed with the command:
```
sudo apt install php-bcmath
```

When checking with the command:
```
sudo apt-cache search php
```

I get a lot of modules installed, also the bcmath:
```
php8.2-bcmath - Bcmath module for PHP
```

However the webservice where this module is required, is failing because of the missing module.
When checking my server with phpinfo:
```
<?php
phpinfo();
?>
```

I can't find it.

Any suggestions on how to resolve this issue?

---

### Post by SeijiSensei on 2023-01-17
Did you restart your apache2 instance after installation?

```
sudo systemctl restart apache2
```

---

### Post by asai on 2023-01-18
> **SeijiSensei said:**
> Did you restart your apache2 instance after installation?

```
sudo systemctl restart apache2
```

Yes. I even restarted the whole server.

---

### Post by asai on 2023-01-18
Solved. Was trouble with different versions of php... :(
Works fine now. :)

---

