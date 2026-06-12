---
title: "WinSCP linux alternative?"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by KyleThe49er on 2008-11-06
I use WinSCP on my schools Windows workstation to connect to their servers. I would like to connect to these same servers using my laptop running Ubuntu 8.04. The "Connect to server" program already on Ubuntu cannot seem to connect. I use a password to login, and it does not ask for one. Are there any programs out there that work the same way and are as easy to use? I would greatly appreciate any recommendations! :)

---

### Post by dannyboy79 on 2009-07-15
> **KyleThe49er said:**
> I use WinSCP on my schools Windows workstation to connect to their servers. I would like to connect to these same servers using my laptop running Ubuntu 8.04. The "Connect to server" program already on Ubuntu cannot seem to connect. I use a password to login, and it does not ask for one. Are there any programs out there that work the same way and are as easy to use? I would greatly appreciate any recommendations! :)
i am looking for an alternate to winscp also because i am trying to connect to my iphone. i have a id_rsa file in my home directory which has a passphrase so when I try to use gftp to connect to iphone i only get to enter one password. and I need to enter 2. one being the passphrase and one being the root password for the iphone. any help would be appreciated.

---

### Post by unlimitedz on 2009-07-15
All you need to do is connect via SSH.  You can use the linux command "scp" to do file transfers between you and the server.
open a terminal and type 

man ssh

---

### Post by SlugSlug on 2009-07-16
I use > places > connect to server > ssh server  and add it to my bookmarks -- very nice

---

### Post by malikjunaid on 2011-01-10
> **SlugSlug said:**
> I use > places > connect to server > ssh server  and add it to my bookmarks -- very nice

Great Tip , I was looking for it since long.
Thanks

---

### Post by Mesqueeb on 2011-01-24
I can not connect to my ipod anymore with the laptop of my brother with windows...
The problem is that my ubuntu computer only has wired internet!!
and when I go to ssh and fill in: ip address, "root" port 22, it fails to connect!!
(and where do I fill in "alpine"??)
Thanks!

---

