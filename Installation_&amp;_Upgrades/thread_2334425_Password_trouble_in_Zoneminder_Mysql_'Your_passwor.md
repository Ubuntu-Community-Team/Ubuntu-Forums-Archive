---
title: "Password trouble in Zoneminder Mysql 'Your password does not satisfy the current...'"
date: 2016-08-19
forum: Installation &amp; Upgrades
---

### Post by sebastien4 on 2016-08-19
I am having problems with my setting up of Zoneminder.

I have a double, quad-core Dell r710 server. 16gigs of RAM. 

Server has 3, 2TB drives set up as RAID 5.

I installed following, by using the Easy Way directions found here:

[https://wiki.zoneminder.com/Ubuntu_Server_16.04_64-bit_with_Zoneminder_1.29.0_the_easy_way](https://wiki.zoneminder.com/Ubuntu_Server_16.04_64-bit_with_Zoneminder_1.29.0_the_easy_way)

1. Installed Basic Ubuntu 16.04 Server, with OpenSSH Server, and LAMP Server and followed the directions until...

2. 'mysql_secure_installation'.  I set up a password.

3. 'apt-get install mysqltuner'. Installed but made no changes.

4. 'apt-get install zoneminder php-gd'. Installed zoneminder. no problems here.

5. 'mysql -uroot -p < /usr/share/zoneminder/db/zm_create.sql'. This is where i get stuck. I get following error when trying to enter password:
"ERROR 1819 (HY000) at line 562: Your password does not satisfy the current policy requirements"

I did begin of install by typing it in (not copy paste). I was very careful not to make mistakes and do not believe i did. I have since figure out how to remotely enter server and am copy pasting commands to avoid any possible errors.

I had changed passwords multiple times. When i create the password, i am given a 100% mark. I have changed the setting to LOW security. Nothing works. Still get this same error line. I am stumped and cannot get any further in install. Any help would be appreciated.

Not sure if this is related, but had many issues with installation of Ubuntu Server. It would boot up to Grub Rescue. I eventually repaired grub with the Grub Boot repair disk. I was then able to start the ZM install until i hit the above password roadblock. When i restarted it the next day, i gave me a basic grub prompt and i could not do anything. I had to run the Grub boot repair disk again. Now It has restarted multiple times no problem.

BTW, i am a novice in linux and learning. So please be as descriptive as possible. Thank you in advance.

---

### Post by sebastien4 on 2016-08-19
Anyone?

---

### Post by mook765 on 2016-08-20
If i would have an answer...
But I don't have.
I see that a ZoneMinder-forum exists.
While waiting here for someone who has experience with ZoneMinder it might be a good idea to look around there and/or place your question there too.
[https://forums.zoneminder.com/]("https://forums.zoneminder.com/")
Kind regards...

---

