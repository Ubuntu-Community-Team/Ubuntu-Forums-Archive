---
title: "Firefox wants to download php files after update to lucid server"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by mhlspn on 2010-05-07
Hello,

I updated from karmic to lucid server edition and now firefox wants to download some php files. index.php which is in the same directory is apparently correctly parsed.

Google chrome tells me that the site may be temporarily down and Opera informs me that the connection has been closed by the remote server.

Under karmic I had a standard lamp server installed and everything worked fine. 

This is the first time I post in a forum and I hope this is fine here.

Any help or ideas are highly appreciated.

Many thanks in advance

PS : I just moved the scripts from the server to a local machine which I updated a couple of weeks ago to lucid and I have the same problem here. I am stuck....

---

### Post by elliotbeken on 2010-05-07
i have has this problem before. all i did was update and restart about 4 days later and it worked.

i was not sure if it was the update or the restarts i did which solved the problem.

sorry but this is prob not much help... 

elliot

---

### Post by dino99 on 2010-05-07
take care of unknown files: install adblock, noscript, gufw (activate it), clamav (8 packages)

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by BbUiDgZ on 2010-05-07
> **mhlspn said:**
> Hello,

I updated from karmic to lucid server edition and now firefox wants to download some php files. index.php which is in the same directory is apparently correctly parsed.

Google chrome tells me that the site may be temporarily down and Opera informs me that the connection has been closed by the remote server.

Under karmic I had a standard lamp server installed and everything worked fine. 

This is the first time I post in a forum and I hope this is fine here.

Any help or ideas are highly appreciated.

Many thanks in advance

PS : I just moved the scripts from the server to a local machine which I updated a couple of weeks ago to lucid and I have the same problem here. I am stuck....


i am no expert by any stretch of the imagination but it sounds like the libapache2-mod-php aint working.

Did you install Apache,Mysql and php from the repo's using apt or do you have a stand alone LAMP stack?

---

### Post by mhlspn on 2010-05-07
> **BbUiDgZ said:**
> i am no expert by any stretch of the imagination but it sounds like the libapache2-mod-php aint working.

Did you install Apache,Mysql and php from the repo's using apt or do you have a stand alone LAMP stack?
Thank you for that idea. I reinstalled libapache2-mod-php5 but the problem persists. 

Google-chrome says that the site was temporarily down. When I reload that page, I come across a mysql error that wasn't there in karmic:

ERROR IN: select * from anni where idanni = 
1064: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1

Warning: mysql_result() expects parameter 1 to be resource, boolean given in....

Any ideas?

PS : Additional information
Apache/2.2.14 (Ubuntu)
MySQL client version: 5.1.41
PHP extension: mysqli

---

