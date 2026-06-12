---
title: "403 You don't have permission to access / on this server for internal ntfs partition"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by teacosy on 2011-05-18
hi...
i am having a problem after the 11.04 upgrade... 

i use an internal ntfs partition for my web root...

when i try to access localhost from a browser, i get: 

403 You don't have permission to access / on this server

and the apache error log shows: 

[error] [client 127.0.0.1] (13)Permission denied: access to / denied

all was working fine for years till the 11.04 upgrade... 

ive tried chmod 755 on the webroot directory... 
when i run: 
ls -l /media/data | grep webroot
i get: 
drwx------ 1 teak teak 8192 2011-05-16 16:26 webroot

im suspecting maybe a policykit thing as after the 9.10 upgrade i had to  enter my password whenever i mounted an internal ntfs partition where  as i didnt before that... since the 11.04 upgrade that has been fixed...  
i refer to this bug: 

[https://bugs.launchpad.net/ubuntu/+source/polkit-kde-1/+bug/575428](https://bugs.launchpad.net/ubuntu/+source/polkit-kde-1/+bug/575428)

any help on this would be great as i want to continue to use this drive for my web root...

thanks

teak

p.s. i also posted a reply here: 
[http://ubuntuforums.org/showthread.php?p=10831330#post10831330](http://ubuntuforums.org/showthread.php?p=10831330#post10831330)

---

