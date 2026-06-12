---
title: "Re-installed ubuntu 8.04 LTS"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by lukydude on 2008-10-14
I just reinstalle dubuntu 8.04... I'm wondering I've installed apache, mysql, php & all ruby ruby on raills and rails stuff I'm wondering how do i acess the programs and make webpages etc.? also I found the web directory for apache but its /var/www wher eonly rooy is allowed to edit... login as root= error the root user can't login - stating ubuntu is broken because the route user can't login thus several programs wil lnot work.

---

### Post by lukydude on 2008-10-14
Any help?

---

### Post by cariboo on 2008-10-14
You can temporarily give your files in /var/www a permission of 777 until you are ready to go live then change the permission back to 755.

Or you can create your pages in your home directory and then copy them to /var/www using sudo.

Jim

---

### Post by lukydude on 2008-10-14
> **cariboo907 said:**
> You can temporarily give your files in /var/www a permission of 777 until you are ready to go live then change the permission back to 755.

Or you can create your pages in your home directory and then copy them to /var/www using sudo.

Jim

How do i do that? I know a few things about Linux and I help people with installations but I'm sorta lost on accessing the directive I've been trying to follow [https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)

---

### Post by lukydude on 2008-10-14
I've used root@luke-desktop-ubuntu:~# sudo chown luke /etc/lighttpd/lighttpd.conf recently would that work for allowing me access to www directory if i adapted it slightly?

---

### Post by lukydude on 2008-10-14
I just can't figure out how towork apche perl ruby on rails or anything else... it's so complicated!... .graaaaa!

---

### Post by lukydude on 2008-10-15
i want to be using ruby on rails, php, mysql & apache but i can't get them to work and yes i do have gcc installed

---

### Post by lukydude on 2008-10-15
oh come on no reply and its been 8 hhours...

---

### Post by lukydude on 2008-10-15
I guess ill drop the issue :(

---

### Post by lukydude on 2008-10-15
support/ community / forum eh? wheres that? i'm left on my own with only 1 reply that doesnt explain it's self very well.

---

### Post by lukydude on 2008-10-16
21 hours no reply... this is getting tiring.

---

### Post by louieb on 2008-10-16
Haven't played with ruby but to get[ my lamp server ]("http://louieb.isa-geek.net/")up and running got most of my hints from this. [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Also search the** how to** and **server **sections of the forum. 

Good Luck.

---

