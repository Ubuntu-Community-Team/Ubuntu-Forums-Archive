---
title: "apache2, PLZ HELP"
date: 2005-11-04
forum: Installation &amp; Upgrades
---

### Post by sunrex on 2005-11-04
i cant install any new files if i add em to var/www/ it wont let me install e107. if i add em to var/www/website/ it says this when i try to view it.

> Forbidden

You don't have permission to access /website/ on this server.
Apache/2.0.53 (Ubuntu) PHP/4.3.10-10ubuntu4.2 Server at 192.168.1.55 Port 80

somone plz tell me how to fix this problem.

phpmyadmin works fine. so wtf is up with this..

---

### Post by kvidell on 2005-11-04
Check the permissions on the files..```
cd /www/website
ls -ldh *
```That'll tell you if they're accesible to the happy world or not.

---

### Post by sunrex on 2005-11-04
> thezombiehunter@thewac:/var/www/website$ ls -ldh *
-rw-------   1 thezombiehunter thezombiehunter  898 2004-03-03 13:23 article.php
-rw-------   1 thezombiehunter thezombiehunter 2.9K 2004-04-26 00:37 backend.php
-rw-------   1 thezombiehunter thezombiehunter 5.7K 2004-05-11 16:10 banner.php
-rw-------   1 thezombiehunter thezombiehunter 2.1K 2004-03-03 14:41 chat.php
-rw-------   1 thezombiehunter thezombiehunter  64K 2004-09-03 11:40 class2.php
-rw-------   1 thezombiehunter thezombiehunter 7.8K 2004-06-06 03:51 comment.php
-rw-------   1 thezombiehunter thezombiehunter  39K 2004-08-31 08:29 content.php
-rw-------   1 thezombiehunter thezombiehunter  18K 2004-09-01 22:42 download.ph                                                                             p
drwx------   3 thezombiehunter thezombiehunter 4.0K 2005-11-04 09:43 e107_admin
-rw-------   1 thezombiehunter thezombiehunter    0 2004-09-17 08:49 e107_config                                                                             .php
drwx------   3 thezombiehunter thezombiehunter 4.0K 2005-11-04 09:43 e107_docs
drwx------  10 thezombiehunter thezombiehunter 4.0K 2005-11-04 09:43 e107_files
drwx------   8 thezombiehunter thezombiehunter 4.0K 2005-11-04 09:43 e107_handle                                                                             rs
-rw-------   1 thezombiehunter thezombiehunter  172 2005-11-04 10:19 e107.htacce                                                                             ss
drwx------  15 thezombiehunter thezombiehunter 4.0K 2005-11-04 09:43 e107_images
drwx------   3 thezombiehunter thezombiehunter 4.0K 2005-11-04 09:43 e107_instal                                                                             l
drwx------  12 thezombiehunter thezombiehunter 4.0K 2005-11-04 09:43 e107_langua                                                                             ges
drwx------  36 thezombiehunter thezombiehunter 4.0K 2005-11-04 09:43 e107_plugin                                                                             s
drwx------  15 thezombiehunter thezombiehunter 4.0K 2005-11-04 09:43 e107_themes
-rw-------   1 thezombiehunter thezombiehunter 3.2K 2004-06-03 20:35 email.php
-rw-------   1 thezombiehunter thezombiehunter 2.1K 2004-09-09 22:58 error.php
-rw-------   1 thezombiehunter thezombiehunter  22K 2004-09-06 05:55 forum.php
-rw-------   1 thezombiehunter thezombiehunter  36K 2004-09-14 08:37 forum_post.                                                                             php
-rw-------   1 thezombiehunter thezombiehunter  17K 2004-09-08 08:02 forum_viewf                                                                             orum.php
-rw-------   1 thezombiehunter thezombiehunter  27K 2004-09-01 09:27 forum_viewt                                                                             opic.php
-rw-------   1 thezombiehunter thezombiehunter 6.2K 2004-09-09 05:31 fpw.php
-rw-------   1 thezombiehunter thezombiehunter 1.2K 2004-08-13 21:48 index.php
-rw-------   1 thezombiehunter thezombiehunter  41K 2004-09-09 22:58 install.php
-rw-------   1 thezombiehunter thezombiehunter  11K 2004-08-31 08:29 links.php
-rw-------   1 thezombiehunter thezombiehunter 3.2K 2004-05-08 17:35 login.php
-rw-------   1 thezombiehunter thezombiehunter 1.9K 2004-08-27 13:31 membersonly                                                                             .php
-rw-------   1 thezombiehunter thezombiehunter  21K 2004-09-09 06:03 news.php
-rw-------   1 thezombiehunter thezombiehunter 3.6K 2004-04-10 22:56 oldpolls.ph                                                                             p
-rw-------   1 thezombiehunter thezombiehunter  11K 2004-05-27 02:46 online.php
-rw-------   1 thezombiehunter thezombiehunter 3.8K 2004-06-05 21:11 print.php
-rw-------   1 thezombiehunter thezombiehunter 1.1K 2004-03-25 00:14 rate.php
-rw-------   1 thezombiehunter thezombiehunter 6.5K 2004-05-25 20:34 request.php
-rw-------   1 thezombiehunter thezombiehunter  241 2004-03-03 13:24 robots.txt
-rw-------   1 thezombiehunter thezombiehunter 7.4K 2004-08-16 13:13 search.php
-rw-------   1 thezombiehunter thezombiehunter  26K 2004-09-06 07:09 signup.php
-rw-------   1 thezombiehunter thezombiehunter 1.1K 2004-09-09 22:58 sitedown.ph                                                                             p
-rw-------   1 thezombiehunter thezombiehunter 4.3K 2004-09-09 05:31 sitemap.php
-rw-------   1 thezombiehunter thezombiehunter  11K 2004-08-14 22:44 stats.php
-rw-------   1 thezombiehunter thezombiehunter  14K 2004-09-07 08:10 subcontent.                                                                             php
-rw-------   1 thezombiehunter thezombiehunter 6.9K 2004-08-12 11:54 submitnews.                                                                             php
-rw-------   1 thezombiehunter thezombiehunter 9.1K 2004-05-13 22:17 top.php
-rw-------   1 thezombiehunter thezombiehunter 1.1K 2004-03-03 13:24 upgrade.php
-rw-------   1 thezombiehunter thezombiehunter 6.8K 2004-09-09 22:58 upload.php
-rw-------   1 thezombiehunter thezombiehunter  15K 2004-09-07 08:30 user.php
-rw-------   1 thezombiehunter thezombiehunter  12K 2004-08-31 08:29 userposts.p                                                                             hp
-rw-------   1 thezombiehunter thezombiehunter  22K 2004-08-28 14:09 usersetting                                                                             s.php


ok..

so what do i do to make em accesible? im on server-only mode...so yea *sigh*

---

### Post by kvidell on 2005-11-04
So's to not cause a major explosion, just adjust one file and see if it helps..

chmod 644 filename.php

Then try viewing it from a browser... If that helps, do it to everything.
- K

---

### Post by kvidell on 2005-11-04
Please Note: Directories need to be 744 to be viewable online. 644 is for files only.
Directories need to be world executable so that you can enter them. That's a 7.
- K

---

### Post by sunrex on 2005-11-04
nope didint help.

my ip is darkworks.no-ip.org if that helps...it doesnt even show in the www folder

---

### Post by sunrex on 2005-11-04
hmm so i cant make a dir in sambar..ok so i typed in mkdir website2...that shows up now... but nothing in it will..

and i get this code...

> 
Warning: main(class2.php): failed to open stream: Permission denied in /var/www/website2/index.php on line 20

Fatal error: main(): Failed opening required 'class2.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/website2/index.php on line 20

---

### Post by kvidell on 2005-11-04
Are you sure you specified the correct RootDocument in the apache conf file?

It seems like Apache is looking for files someplace other than where you'd like to put them.

I believe the default is /var/www or /var/html.. but it's been awhile and I'd rather not install apache on my laptop, lol.
- Kev

---

### Post by sunrex on 2005-11-04
its as it came. i couldent find what to edit in the apache.conf...

from what i saw in the apache.conf it is var/www/, so how do i add files....*sigh*

yes this is my first try at a webserver in ubuntu...

---

### Post by kvidell on 2005-11-04
[QUOTE=sunrex]its as it came. i couldent find what to edit in the apache.conf...

from what i saw in the apache.conf it is var/www/, so how do i add files....*sigh*

yes this is my first try at a webserver in ubuntu...[/QUOTE]
Unless you chown /var/www to your user and make files world readable, and directories world executable, you'll need to be root to manage it.

Move the files you want to be viewable on the internet to /var/www under whatever directory structure you wish.
- Kev

---

### Post by sunrex on 2005-11-04
[QUOTE=kvidell]Unless you chown /var/www to your user and make files world readable, and directories world executable, you'll need to be root to manage it.

Move the files you want to be viewable on the internet to /var/www under whatever directory structure you wish.
- Kev[/QUOTE]

they are in /var/www, i can see website2, i cannot see the files in it and i get that error.

---

### Post by sunrex on 2005-11-04
ok i think i got it, thks for the chmod suggestion..quick question........how do i chmod a hole freekin directory with 50 files in it =/ plz tell me its not hand to hand..

---

### Post by kvidell on 2005-11-04
You can use asterises.
chmod 644 *.php
chmod 644 *

Just be sure that if you catch any directories in that you take care of them seperately (chmod 744 directory-name)
- K

---

