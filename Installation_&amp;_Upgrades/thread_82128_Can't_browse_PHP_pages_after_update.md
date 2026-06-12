---
title: "Can't browse PHP pages after update"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by ytseshred on 2005-10-25
I've updated to Breezy successfully.  I then installed php5, libapache2-mod-php5, but now when I go to my webpages that are php pages, instead of getting the webpage, my server is trying to send the client the .php file.  As in, when I go to ./my_page.php, the browser tries to download my_page.php.

Anyone have any ideas on what I should check to see what's going wrong?  Thanks.

---

### Post by ytseshred on 2005-10-25
Just realized, that for some reason, it didn't properly install the php5.conf and php5.load files in /etc/apache2/mods-enabled.  I'm going to try to copy these from another server and see if that works.

---

