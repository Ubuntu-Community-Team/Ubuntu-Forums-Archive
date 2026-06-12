---
title: "WordPress  Installation"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by stamatiou on 2010-11-07
Hey guys, can anyone tell me how to install WordPress on Ubuntu 10.10?

---

### Post by geoffmcc on 2010-11-07
wow, i never thought to look if it was in repository before and it is. But i always just download the tar.gz from website and run the php install process threw browser

---

### Post by stamatiou on 2010-11-07
> **geoffmcc said:**
> wow, i never thought to look if it was in repository before and it is. But i always just download the tar.gz from website and run the php install process threw browser
I didn't understand nothing.....

---

### Post by geoffmcc on 2010-11-07
im saying you can install wordpress threw apt-get, although i have not done it that way before.

I always just go to wordpress website. Download, unzip and place in /var/www/wordpress

then just go to domain.com/wordpress and go threw the installer

---

### Post by stamatiou on 2010-11-07
> **geoffmcc said:**
> im saying you can install wordpress threw apt-get, although i have not done it that way before.

I always just go to wordpress website. Download, unzip and place in /var/www/wordpress

then just go to domain.com/wordpress and go threw the installer
The only thing I understood is the apt -get part........

---

### Post by wongo888 on 2010-11-07
Assuming you have a working server that is just needing wordpress. Open a terminal window and type the following:

```

$ sudo apt-get install wordpress

```

Then follow these instructions from the main wordpress website:

"Run the WordPress installation script by accessing wp-admin/install.php in a web browser.
If you installed WordPress in the root directory, you should visit: 

```
http://example.com/wp-admin/install.php
```

If you installed WordPress in its own subdirectory called blog, for example, you should visit: 

```
http://example.com/blog/wp-admin/install.php
```

That's it! WordPress should now be installed."

[http://codex.wordpress.org/Installing_WordPress#Detailed_Instructions](http://codex.wordpress.org/Installing_WordPress#Detailed_Instructions)

If you need help setting "everything" then there are more than a few tutorials on this topic.

[http://www.debianadmin.com/install-wordpress-in-debian-etch.html](http://www.debianadmin.com/install-wordpress-in-debian-etch.html)

---

