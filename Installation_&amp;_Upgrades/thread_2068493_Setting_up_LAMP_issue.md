---
title: "Setting up LAMP issue"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by Chuckymong on 2012-10-09
Hello, I am glad to say that I have finally managed to get lubuntu installed on my machine. The next step was for me to install and configure LAMP. I have successfully setup apache2 and php5, but after installing mysql and begining to configure it I keep getting the same error when putting anything using the mysql extension into my php code. The error im getting is -

"HTTP Error 500 (Internal Server Error): An unexpected condition was encountered while the server was attempting to fulfil the request."

I cannot understand why this is happening. If i remove anything mysql related from the script it works just fine.

Thanks Marcus.

EDIT: I have just set up error reporting only to find that im getting the fatal error call to undefined function - mysql_connect()

Thanks again

---

### Post by Chuckymong on 2012-10-09
Sorry for the bump but have more information that might help someone help me and I couldn't edit twice.

I figured this must be down to the - extension=mysql.so - part of the php.ini file. I thought the file was not being found, so i did a basic search of my lubuntu to find if the file even existed on my machine using some of the basic command line stuff I know -

```
sudo find / 'mysql.so'
```

I found that the file does not exist on my machine. I then consulted Google on how I could get this file but couldn't find anything. Hope this has narrowed my problem down.

Thanks Marcus.

EDIT: Fixed the problem i had installed the standard php not the php5-mysql. Silly mistake sorry for wasting time.

---

