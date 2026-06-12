---
title: "Upgrade to 11.04 not working"
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by JJJollyjim on 2011-09-03
I have just installed Ubuntu 10.10 on a MacBook (with refit). When I try to upgrade to 11.04 (with the update manager or the do-release-upgrade command) I get this error:


```
Could not download the upgrades 

The upgrade has aborted. Please check your Internet connection or 
installation media and try again. All files downloaded so far are 
kept. 

Failed to fetch 
http://nz.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu1_i386.deb 
404 Not Found 
Failed to fetch 
http://nz.archive.ubuntu.com/ubuntu/pool/universe/i/ibus-pinyin/ibus-pinyin-db-open-phrase_1.3.11-1_all.deb 
404 Not Found 
Failed to fetch 
http://nz.archive.ubuntu.com/ubuntu/pool/universe/v/vala-0.10/libvala-0.10-0_0.10.4-1ubuntu1_i386.deb 
404 Not Found 
Failed to fetch 
http://nz.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-100dpi/xfonts-100dpi_1.0.3_all.deb 
404 Not Found 
Failed to fetch 
http://nz.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-75dpi/xfonts-75dpi_1.0.3_all.deb 
404 Not Found 



Restoring original system state
```

Would switching to a non-New Zealand server help? How would I do this? Thanks.

---

### Post by 2F4U on 2011-09-04
I checked the first entry on the NZ server and it is not there. So for this and probably all other entries it would help to change download servers. Package management provides an option to select a repository server. You can, for example, choose the main server. Another option is to open /etc/apt/sources.list and change every occurrence of nz.archive.ubuntu.com to, for example, archive.ubuntu.com.

---

### Post by Hakunka-Matata on 2011-09-04
> **JJJollyjim said:**
> I have just installed Ubuntu 10.10 on a MacBook (with refit). When I try to upgrade to 11.04 (with the update manager or the do-release-upgrade command) I get this error:


```
Could not download the upgrades 

The upgrade has aborted. Please check your Internet connection or 
installation media and try again. All files downloaded so far are 
kept. 

Failed to fetch 
http://nz.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu1_i386.deb 
404 Not Found 
Failed to fetch 
http://nz.archive.ubuntu.com/ubuntu/pool/universe/i/ibus-pinyin/ibus-pinyin-db-open-phrase_1.3.11-1_all.deb 
404 Not Found 
Failed to fetch 
http://nz.archive.ubuntu.com/ubuntu/pool/universe/v/vala-0.10/libvala-0.10-0_0.10.4-1ubuntu1_i386.deb 
404 Not Found 
Failed to fetch 
http://nz.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-100dpi/xfonts-100dpi_1.0.3_all.deb 
404 Not Found 
Failed to fetch 
http://nz.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-75dpi/xfonts-75dpi_1.0.3_all.deb 
404 Not Found 



Restoring original system state
```[COLOR=Red]Would switching to a non-New Zealand server help? How would I do this? Thanks.[/COLOR]


[LIST]
[*]Open **Synaptic**,
[*]chose **settings**
[*]chose **repositories**
[*]click the down pointing arrow in **Download from box:**
[*]chose **Other**
[*]chose **Select Best Server**
[*]wait for **Testing download servers **task to finish.
[*]click **Close **when satisfied.
[/LIST]

---

