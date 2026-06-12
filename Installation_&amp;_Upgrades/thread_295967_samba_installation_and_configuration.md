---
title: "samba installation and configuration"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by wufei on 2006-11-08
hello. im a newbie in linux and wanted to expore the great world of it. i had a problem that i cannot solve. i had installed a ubuntu lts 6.06.1 lts. installed it with lamp. 

my problem is this
1. how can i install a samba server
2. i plan to make my computer a file,printer,domain controller server
3. how can i configure it to make shared folders with authentication, read write permissions to windows xp users. there would be 40 users connecting to my computer.
4. if domain controller isnt possible, you can skip it.

thank you for the help...:KS :KS :KS

---

### Post by MyAnda on 2006-11-08
hava a look at
[http://ubuntuguide.org/wiki/Ubuntu_dapper#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_dapper#Samba_Server)
[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10) (should still have some relevant info)

---

### Post by mssever on 2006-11-08
To install Samba, do ```
sudo apt-get install samba
```
Samba's config lives in /etc/samba/smb.conf. You can find documentation for smb.conf by typing ```
man smb.conf
```

It's possible to do everything you want with samba--including a domain controller--but I don't know off the top of my head how to do it. When I set up samba on my server, I read the documentation (as well as the samba website) and figured it out from there. Hope this helps.

---

