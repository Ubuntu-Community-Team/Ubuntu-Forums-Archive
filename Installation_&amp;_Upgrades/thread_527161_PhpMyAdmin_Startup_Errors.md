---
title: "PhpMyAdmin Startup Errors"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by meantone on 2007-08-16
Hi,

I've got LAMP and Drupal running on Feisty Fawn/GNome. To simplify some tasks and to follow tutorials I installed PhpMyAdmin using "sudo apt-get" command.  I was able to set the password, but now I'm getting the following three errors when launching from Localhost: 

[INDENT]Warning: session_write_close() [function.session-write-close]: open(/var/lib/php5/sess_nof7ayRa1WeH66wFXxarFLPR,Ec, O_RDWR) failed: Permission denied (13) in /usr/share/phpmyadmin/libraries/common.lib.php on line 1152

Warning: session_write_close() [function.session-write-close]: Failed to write session data (files). Please verify that the current setting of session.save_path is correct (/var/lib/php5) in /usr/share/phpmyadmin/libraries/common.lib.php on line 1152

Warning: Cannot modify header information - headers already sent by (output started at /usr/share/phpmyadmin/libraries/common.lib.php:1152) in /usr/share/phpmyadmin/libraries/common.lib.php on line 1159[/INDENT]

I've been scouring the internet and forums, but havent' found anything that specifically addresses this issue.

Thanks!

PS: Please be advised I'm a Windoze guy.

---

### Post by Hugolp on 2007-08-19
This might help you: [http://ubuntuforums.org/showthread.php?t=455362&highlight=phpmyadmin&page=1](http://ubuntuforums.org/showthread.php?t=455362&highlight=phpmyadmin&page=1)

Hugo

---

### Post by raashell on 2007-10-09
Meantone,

     Hopefully you've figured this out by now.   :)  I had very similar errors than you.  What I discovered was that my permissions for the folders with PHP stuff were not enabled for me.  For you, these would be:


var/lib/php5
/usr/share/phpmyadmin/libraries/

   What I did to fix this: 

   a. I pressed alt-f2, typed in "gksudo nautilus"
   b. navigated to these folders
   c. right clicked them, changed the tab to permissions.
   d. and altered the permissions to allow me to read and write, create and delete. 
   e. I told them to apply this to every file within these folders.

   After that, it loaded fine.  This is a shotgun approach from someone who is largely linux ignorant.  I'm sure there is a better way and I hope that someone says what it is.  :)  In fact, this could be potentially harmful, but it is what worked for me.

  Good Luck!

John

---

