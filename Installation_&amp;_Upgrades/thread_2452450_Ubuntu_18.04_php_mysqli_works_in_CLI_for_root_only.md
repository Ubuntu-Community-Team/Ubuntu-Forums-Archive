---
title: "Ubuntu 18.04: php mysqli works in CLI for root only"
date: 2020-10-22
forum: Installation &amp; Upgrades
---

### Post by Elmi77 on 2020-10-22
Hi,

I have the weird situation that PHP-scripts that make use of mysqli-functions work in CLI only for root but not for other users. That's what I have:

1. A script containing following code:
[PHP]if (!extension_loaded('mysqli'))
{
   echo "load mysqli.so";        
   dl('mysqli.so');
}?>[/PHP]

When root calls "php test.php" in CLI, it is executed successfully, nothing is printed to the console. When an other user is executing this script, following error is shown:
```
Warning: dl(): Unable to load dynamic library 'mysqli.so' (tried: /usr/lib/php/20170718/mysqli.so (/usr/lib/php/20170718/mysqli.so: undefined symbol: mysqlnd_global_stats), /usr/lib/php/20170718/mysqli.so.so (/usr/lib/php/20170718/mysqli.so.so: cannot open shared object file: No such file or directory)) in /home/oxy/test.php on line 4

```

The user is member of mysql-group

2. When executing such scripts via Webbrowser/Apache2, everything works fine

3.  /etc/php/7.2/cli/ is symlinked to  /etc/php/7.2/apache2/ to ensure both make use of the same configuration

4. When calling php -i, it tells me the ini-files in  /etc/php/7.2/cli/ are used

So...any idea why only few users are allowed to execute PHP-scripts?

Thanks!

---

