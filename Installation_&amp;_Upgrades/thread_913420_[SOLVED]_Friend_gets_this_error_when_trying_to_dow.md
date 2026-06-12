---
title: "[SOLVED] Friend gets this error when trying to download from my folderon apache2"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by lowstand on 2008-09-07
High i am having an issue not sure what i done wrong or what i am running apache2 on my Ubuntu i have my website up runing smooth a friend needed a file so i dropped it in a folder i made in mysite directory an called it downloads an just dropped the taz file in he get this error i try an hit it from the gateway address as as well i get the same reply how do i fix please in the easiest terms possible i know i installed a ftp as well but have no clue where to find it eather lmao
but would love to get this error fixed so he may download from me or anyone else as well thanks


Fobidden
You don't have permission to access /downloads/ on this server.

Apache/2.2.8 (Ubuntu) mod_ssl/2.2.8 OpenSSL/0.9.8g Server at lowstand.dyndns.org Port 80


i have posted this in server area as well never got an answer 

thanks

---

### Post by DGortze380 on 2008-09-07
> **lowstand said:**
> High i am having an issue not sure what i done wrong or what i am running apache2 on my Ubuntu i have my website up runing smooth a friend needed a file so i dropped it in a folder i made in mysite directory an called it downloads an just dropped the taz file in he get this error i try an hit it from the gateway address as as well i get the same reply how do i fix please in the easiest terms possible i know i installed a ftp as well but have no clue where to find it eather lmao
but would love to get this error fixed so he may download from me or anyone else as well thanks


Fobidden
You don't have permission to access /downloads/ on this server.

Apache/2.2.8 (Ubuntu) mod_ssl/2.2.8 OpenSSL/0.9.8g Server at lowstand.dyndns.org Port 80


i have posted this in server area as well never got an answer 

thanks

I don't know much about apache, but it sounds like a simple permissions issue. You have to give "Others" sufficient access to that folder. try chmod 775

---

### Post by lowstand on 2008-09-07
> **DGortze380 said:**
> I don't know much about apache, but it sounds like a simple permissions issue. You have to give "Others" sufficient access to that folder. try chmod 775

how do i get to it  an lol i guess that would be terminal command i can't do it from folder tried it didn't work i think its got something to do with the ssl i installed but never conf'd it cause i don't know how lol

---

### Post by mbeach on 2008-09-07
You posted in the server area 2 hours ago, with the correct answer there now.  As Dgortze380 suspected, it is a permissions issue, however, the best approach is likely to change the ownership of the file to www-data instead of changing the permissions.

see 
[http://ubuntuforums.org/showthread.php?t=913389](http://ubuntuforums.org/showthread.php?t=913389)

---

