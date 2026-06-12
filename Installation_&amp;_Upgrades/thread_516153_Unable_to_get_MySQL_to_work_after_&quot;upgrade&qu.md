---
title: "Unable to get MySQL to work after &quot;upgrade&quot;"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by nomaam on 2007-08-02
Hello:

I was running MySQL on Ubuntu 7.04 LAMP with no problems until I ran apt-get upgrade, now I can't even start MySQL. MySQL version is now: 5.0.3.38

I get an error telling me "database list could not be found" through the Webmin program I'm using when I try to start it. 

I assume the paths in the config file have been changed, but I do not know what I should be changing.

I have checked my config file and it states that the socks being used are located at:

/var/run/mysqld/mysqld.sock

However, there is no file in that directory and if I create one and try to start MySQL then the file is deleted some how. I have also conducted a search on my computer and there is no mysqld.sock or mysql.sock file even on my computer.

I have tried to "purge" my MySQL installation and reinstall but MySQL continues to fail to start when I start my machine. 

I have no idea where the MySQL logs are or where any systems logs are and I don't know how to obtain any more information on this problem. 

Could someone please advise me on how to fix this problem short of reinstalling the whole OS...

Thanks.

---

