---
title: "upgrade to lucid - LAMP problems (php not parsed)"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mikio on 2010-03-21
hi everyone,

i have apche2 and libapache2-mod-php5 installed and i have the php5 modules installed. i double checked that by doing:

$sudo a2enmod php5
-> Module php5 already enabled

and also:
$sudo /etc/init.d/apache2 restart

yet, when i try load one of my php enabled webpages it downloads the file. clearly it is not parsing the php.

needles to say - this did work before the upgrade. i also tried to boldly remove lamp altogether. then reinstall it. did not work. i also purged/reinstalled apcahe2 and libapache2-mod-php5 - did not help

many thanks for any hints!

ps: some noteworthy information:
my upgrade was very bumpy! it downloaded everything but failed midway. it did not install gnome! and my network cards did not work! i had to manually install gnome. and then still 'half' the desktop was not working/buggy. i used 'tasksel' to remove/reinstall ubuntu-desktop and that solved my problems. 
though i have to install some programs manually now - eg: thunderbird was not installed by default. 
note that configurations files are not touched by that. so, it is safe in that respect..

---

### Post by phillw on 2010-03-21
Hi,

I recall this horror !!

Head over to [http://support.mozilla.com/tiki-view_forum_thread.php?forumId=1&comments_threshold=0&comments_parentId=1452&comments_offset=40&comments_per_page=20&thread_style=commentStyle_plain](http://support.mozilla.com/tiki-view_forum_thread.php?forumId=1&comments_threshold=0&comments_parentId=1452&comments_offset=40&comments_per_page=20&thread_style=commentStyle_plain)

And follow the instructions in the last posting. The one that sorted it for me was clearing all history / cookies and cache.

Once it trips in for a site, clearing the cache etc. cleared it for me, I haven't seen it in a while.

If you're still having problems, install the chromium browser and see if chromium also has the problem. That will let you know if it is your LAMP installation or FFox having a hissy fit.

If it is the LAMP, then clear Apache, MySQL and PHP. Then use ```
sudo tasksel
``` and install LAMP that way - I have battled LAMP installations before, when people have done it the manual way. Use Synaptics to install PhpMyAdmin, again I have had battles when people have done it using apt-get.

P.S. If you look at the 2nd posting here --> [http://forum.phillw.net/viewtopic.php?f=4&t=4](http://forum.phillw.net/viewtopic.php?f=4&t=4)  You'll see my thoughts on the crazy way that Ubuntu still installs magic-quotes=on in the php.ini file.

Regards,

Phill.

---

### Post by mikio on 2010-03-21
well, the problem is not the browser really. the problem is todo with how apache is serving the file. it is definitely not parsing/executing the php but serving the php file in clear text. (i double checked by downloading and viewing the file)

[i did double check with a second browser - epiphany. same problem there]

any other comments?

---

### Post by mikio on 2010-03-21
SOLVED THE PROBLEM!

i followed the instructions on this page:

[http://marco.tondela.org/2010/03/your-public_html-with-php5-isnt-working-in-ubuntu-lucid/](http://marco.tondela.org/2010/03/your-public_html-with-php5-isnt-working-in-ubuntu-lucid/)

in particular, editing this file:

$sudo vim /etc/apache2/mods-enabled/php5.conf

and commenting these lines:

#    <ifmodule  mod_userdir.c>
#        <directory /home/*/public_html>
#            php_admin_value engine Off
#        </directory>
#    </ifmodule>

please refer to the original article for full details. (i also did have to clear the cache/history for firefox to take notice .. )

hope this helps..

---

### Post by kss18 on 2010-03-24
This saved my day. I had exactly the same problem, phpinfo() worked in the /var/www directory but not in ~user/public_html/.

Thank you for posting the link to Marco's blog entry.

krishna

---

### Post by nooga on 2010-03-26
I did that and still php won't execute in ~/public_html

+ my .htaccess files seem to work incorrectly.

Please help, I must codeeee ;[

---

