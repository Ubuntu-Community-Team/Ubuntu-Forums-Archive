---
title: "Server + LAMP Server ?"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by albertc on 2006-12-02
Hi

I've been using Ubuntu Desktop for a while and now I want to move to Ubuntu also for my server. What I want is a machine for sharing files, printers, fax AND a web server (w/ Apache, MySQL and PHP).

However, I'm still wondering if this can be done. Both the Ubuntu Server CD install and the web documentation are mentioning the LAMP install as an ALTERNATIVE to the regular Server install. Isn't there a way to have Server+LAMP Server on the same machine? (and I mean  concurrently, not as a dual-boot setup).

Thanks in advance for any assistance
--
Albert

---

### Post by indytim on 2006-12-02
I don't have the server version installed currently.  I though that the LAMP server came with the standard Ubuntu Server install.  

IndyTim

---

### Post by albertc on 2006-12-02
IndyTim,

Do you mean that the standard Ubuntu Server install does indeed install a LAMP server too? If so, why is a LAMP server install offered as an alternative at boot-time? Which server features are NOT installed then if one chooses the LAMP server option?

Thanks
--
Albert

---

### Post by indytim on 2006-12-02
Albert,

As I mentioned originally, I currently do not have the Ubuntu Server installed on the active box. I have read in numerous places, that at the time of the server install, you can elect to have the full LAMP package installed along with whatever other options are available in the server install.

For a more authoratitive answer, you might swing over to the Programming forum.  A lot of the server folks lurk around there.

IndyTim

---

### Post by az on 2006-12-02
> **albertc said:**
> IndyTim,

Do you mean that the standard Ubuntu Server install does indeed install a LAMP server too? If so, why is a LAMP server install offered as an alternative at boot-time? Which server features are NOT installed then if one chooses the LAMP server option?

Thanks
--
Albert

A "server" install is just a base system.  A LAMP install is just a server install with apache2 php5-mysql libapache2-mod-php5 mysql-server installed for you - you get the same thing if you install a base system and add those packages on later.

You can install the LAMP stack on a desktop system if you want - they do not conflict with one another.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

