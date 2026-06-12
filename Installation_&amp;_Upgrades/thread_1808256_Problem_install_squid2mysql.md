---
title: "Problem install squid2mysql"
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by iniwidi on 2011-07-20
I have idea to point access.log from squid to database, n i have read the article about it, heres the article [http://sqls.net/wiki/howto:log_squid_to_mysql](http://sqls.net/wiki/howto:log_squid_to_mysql)

the step is :
**1. Squid.conf**

    Find the log section of you squid file and add/change these lines: 
    logformat custom %{%Y-%m-%d %H:%M:%S}tl   %03tu %>a %>A %<A %la %lp %tr %{Referer}>h  %{User-Agent}>h %{Server}<h %un %ul %ui %Hs %mt %rm %ru %rv  %<st %Sh %Ss   cache_access_log  /var/log/squid/access.log custom 
   You could use any format you want honestly.  But this is what I am using. 
  
  **2. Create mysql DB for Squid**

    Yea, sure.. someday I'll export the schema.  Meanwhile you'll have to look at the script and build an appropriate DB for it. 
  
  **3. squid2mysql.pl**

    Download [http://sqls.net/files/squid2mysql.pl](http://sqls.net/files/squid2mysql.pl) and install it to /opt/squid2mysql 
  
  **4. Gentoo init.d Script**

    Download [http://sqls.net/files/squid2mysql](http://sqls.net/files/squid2mysql) and copy it to /etc/init.d 
  
  **5. Set it to run at boot**

     # rc-update add squid2mysql default 
  
  **6. Restart/start Squid**

    /etc/init.d/squid restart 
  
  **7. Start Squid2MySQL**

    /etc/init.d/squid2mysql start 



EOF

  

And i have error at the step 4, heres the error show :

# /etc/init.d/squid2mysql start
bigger 50
script "/etc/init.d/squid2mysql" line 6: unknown command "depend()"

My qustion :

What shell gentoo use ? how to convert the script from gentoo to ubuntu ?

Thx'
Widianto

---

