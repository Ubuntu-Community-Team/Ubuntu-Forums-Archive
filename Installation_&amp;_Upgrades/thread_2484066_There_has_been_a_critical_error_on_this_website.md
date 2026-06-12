---
title: "There has been a critical error on this website"
date: 2023-02-16
forum: Installation &amp; Upgrades
---

### Post by Rui_Brcia on 2023-02-16
[COLOR=#32373C][FONT=&quot]Hi all,[/FONT][/COLOR]
[COLOR=#32373C][FONT=&quot]I have upgrade Ubuntu Server from 18.04 to 22.04 and i have any error since i reinstall the phpmyadmin.
“There has been a critical error on this website. Please check your site admin email inbox for instructions.”

It is possible to be any old plugin on Wordpress to do this? Any ideas how to fix this? Apache is running as well as PHP and Mysql.
rbarcia.pt (My site)

This is part of the debug.log:

```
Fatal error: Uncaught Error: Class “WPGMZA\Integration\Gutenberg” not found in /var/web/rbarcia.pt/httpdocs/wp-content/plugins/wp-google-maps/includes/class.plugin.php:82 Stack trace: #0 [internal function]: WPGMZA\Plugin->__construct() #1 /var/web/rbarcia.pt/httpdocs/wp-content/plugins/wp-google-maps/includes/class.factory.php(55): ReflectionClass->newInstanceArgs() #2 /var/web/rbarcia.pt/httpdocs/wp-content/plugins/wp-google-maps/includes/class.plugin.php(474): WPGMZA\Factory::createInstance() #3 /var/web/rbarcia.pt/httpdocs/wp-content/plugins/wp-google-maps/includes/class.plugin.php(481): WPGMZA\create() #4 /var/web/rbarcia.pt/httpdocs/wp-includes/class-wp-hook.php(308): WPGMZA{closure}() #5 /var/web/rbarcia.pt/httpdocs/wp-includes/class-wp-hook.php(332): WP_Hook->apply_filters() #6 /var/web/rbarcia.pt/httpdocs/wp-includes/plugin.php(517): WP_Hook->do_action() #7 /var/web/rbarcia.pt/httpdocs/wp-settings.php(480): do_action() #8 /var/web/rbarcia.pt/httpdocs/wp-config.php(89): require_once(‘…’) #9 /var/web/rbarcia.pt/httpdocs/wp-load.php(50): require_once(‘…’) #10 /var/web/rbarcia.pt/httpdocs/wp-blog-header.php(13): require_once(‘…’) #11 /var/web/rbarcia.pt/httpdocs/index.php(17): require(‘…’) #12 {main} thrown in /var/web/rbarcia.pt/httpdocs/wp-content/plugins/wp-google-maps/includes/class.plugin.php on line 82

```
I also rename the plugin file and still no clue... The error stils there.

Regards[/FONT][/COLOR]

---

### Post by TheFu on 2023-02-17
> **Rui_Brcia said:**
>  
It is possible to be any old plugin on Wordpress to do this? Any ideas how to fix this? Apache is running as well as PHP and Mysql. 

Yes, old code written for a different php version will likely break.  The versions of mysql, php and apache are very different between those 2 releases.  

I'm not a Php-LAMP person, so I can't help with specific errors. To me, LAMP is for perl. ;)

BTW, when ever posting terminal output, like errors, please, please, please, use the forum code tags so formatting is retained.

---

### Post by SeijiSensei on 2023-02-17
Do you have another location on the server you can visit that doesn't use WordPress?

If so, I'd create a file, info.php, like this:

```
<?php phpinfo() ?>
```

and put it in a publicly-visible directory. Then open a browser and view it over the Internet. You'll see everything you need to know about versions and modules.

---

### Post by Rui_Brcia on 2023-02-17
Hi,

Thanks for help.
I have creat a info.php. So now what i should look for? if its a old plugin how can i disable it since i cant enter in dashboard on wordpress?

Regards

---

