---
title: "Proftp, different folders for different users"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by Black_Moon on 2010-02-18
I'm using ProFTP on Ubuntu 8.04 machine

I don't need anonimous users, i need to create access to different folder from different user

For example - user1 can login only in /folder1
user2 - only in /folder2

how to write it in config file?

current options are - 

DefaultRoot            /media/public    

<Limit LOGIN>
AllowUser user1 user2
DenyALL
</Limit>


<Directory /media/public>
Umask 000 000 #test mode
AllowOverwrite on

</Directory>

---

