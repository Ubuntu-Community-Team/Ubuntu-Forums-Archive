---
title: "Disable Directory Browsing in Apache (Ubuntu 7.04)"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by textguru on 2007-07-03
Have installed Ubuntu Server 7.04 and wanting to disable Directory Browsing. Can you help me on this?

---

### Post by textguru on 2007-07-05
have found article about this: [http://ubuntuforums.org/showthread.php?t=255446](http://ubuntuforums.org/showthread.php?t=255446)

What needs to be changed on the config file?

---

### Post by scragar on 2007-07-05
the easiest method might using .htaccess as follow:

```
RewriteEngine on
RewriteRule (\/|\/?(.*))$ http://yoursite.com/404.php
```
change the [http://yoursite.com/404.php](http://yoursite.com/404.php) file to the page you want to show people if they try to open a directory and your all done.

---

### Post by textguru on 2007-07-05
> **scragar said:**
> the easiest method might using .htaccess as follow:

```
RewriteEngine on
RewriteRule (\/|\/?(.*))$ http://yoursite.com/404.php
```change the [http://yoursite.com/404.php](http://yoursite.com/404.php) file to the page you want to show people if they try to open a directory and your all done.
where can I find .htaccess?

---

### Post by scragar on 2007-07-05
it's normaly in the root directory of your website(usualy called htdocs or www), because it begins with a . it's a hidden file so you may have to press ctrl+H to show hidden files.

if it's not there then you can create it and just put that content in it.

---

