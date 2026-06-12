---
title: "chown -R www-data:www-data /usr/share/wordpress - Operation not permitted"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by DanSpec on 2010-10-09
Hi all, and thanks in advance for any help you offer. 

Recently I installed Wordpress/lamp/mysql on my ubuntu lucid installation (I followed this well written article [https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)).

All went well, except for when I ran:

chown -R www-data /usr/share/wordpress

**I got**

chown: changing ownership of `/usr/share/wordpress': **Operation not permitted**

on all the files in the wordpress directory... 

Next after some research

**I tried:**

chown -R www-data:www-data /usr/share/wordpress
chown -R dan:www-data /usr/share/wordpress
sudo chown -R www-data:www-data /usr/share/wordpress

**Same results everytime, "Operation not permitted" on all files in the wordpress directory**

Next I stopped the apache service and tried all of the above and it I got the same "Operation Failed" error everytime. I searched, google, bing and even dogpile four or five times.. Found one post that said if my disk was fat32 it could be causing the problem. So I checked and made sure the disk is ext2/ext3.

**How can I get these permissions set?**

From what I have read this is why when I go to the wordpress web gui and try to upgrade anything it fails and says I am using the wrong password.. Even when I have used my WP username/password, and my user account. Nothing has worked so far.

**If anyone has an idea or knows how to fix this - please let me know.**

Kind regards,

Dan

:guitar: <-- Any other guitar players out there? If so check out my working blog at danspec.com - and get riffworks so we can jam!

---

### Post by b1tchacked on 2012-06-24
sudo chown -R dan:www-data /usr/share/wordpress


I assume that dan is your username ... that would do as far as i know!..
Tell me , if you still have issues..

If the problem persists , try removing -R , to figure out whether it works on files on one level at the least.

---

### Post by oldos2er on 2012-06-24
Old thread closed.

---

