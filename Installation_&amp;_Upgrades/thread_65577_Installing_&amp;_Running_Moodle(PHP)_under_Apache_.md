---
title: "Installing &amp; Running Moodle(PHP) under Apache 2 &amp; MySQL 4.1"
date: 2005-09-14
forum: Installation &amp; Upgrades
---

### Post by rexx on 2005-09-14
I've been trying to install the Moodle platform in these past couple of days, with no success...

I first tried the package that was available in the repositories but after installing (following the install guide, etc...) the php pages would show up blank... I reviewed the setup and reconfigured it all over again... uninstalled, installed several times... 

Then I thought about downloading the most recent version from moodle.org and installing it and configure step by step and guess what... same result.

I tried adding the command 'phpinfo()' to the index.php and result was positive, wich made me think that apache was well configured (btw, I'm running apache2). Then I checked the database settings (running MySql 4.1) everything seems to be ok there, the user and pass are correct and working... 

The last possible problem I thought of... it would be permissions, I've checked the moodle folders, apache2 and mysql and they're all running under root.root

I'm running out of time and ideas... if someone could help me out, that would really be something!

Tnks in advanced

---

### Post by oly on 2005-10-20
i have had exactly the same problem, i was running moodle on hoary did a backup and restored it in breezy, but pages came up blank thinking something may be wrong with what i did i have since reinstalled the OS, still no luck even using the repository version.

also using apache2 and mysql 4.1, think my next step is to try the older apache and see if it runs.

---

### Post by paulr on 2006-10-29
Just written today ; MoodleSQL on Edgy. Should work on Dapper. Might work on the earlier ones (maybe using PHP4)

[https://help.ubuntu.com/community/MySQLMoodle](https://help.ubuntu.com/community/MySQLMoodle)

---

### Post by Abhi Kalyan on 2006-11-04
Am installing PHP on Apache with MTSQL, So am watching this thread for help.
Thank you

---

