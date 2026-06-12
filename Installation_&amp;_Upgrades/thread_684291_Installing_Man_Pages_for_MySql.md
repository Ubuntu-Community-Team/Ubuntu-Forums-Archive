---
title: "Installing Man Pages for MySql"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by alex81 on 2008-01-31
Hello all, 

I am new to Ubuntu and Linux in general. I am currently trying to figure out how to install the man pages that I have downloaded from MySql's web site. They all end with a ".1" extension. 

Any help would be greatly appreciated. 

Thanks, 
Alex.

---

### Post by lsmobrian on 2008-01-31
Are they not already on your computer (assuming you have mysql installed) try 'man mysql' in a terminal

---

### Post by alex81 on 2008-01-31
Hello,

Thanks for your reply.

No they are not installed - I tried it. I only installed the mysql client on the machine in question. Maybe its when you install the server package.

Any further suggestions would be greatly appreciated.

Thanks.

> **lsmobrian said:**
> Are they not already on your computer (assuming you have mysql installed) try 'man mysql' in a terminal

---

### Post by lsmobrian on 2008-02-01
I am currently on a fedora box, but i found my mysql man page here

/usr/share/man/man1/mysqlman.1.gz

i dont know how man works as far as updating what man pages it has, but maybe if you jsut copy it there it will work (assuming thats where ubuntu puts man pages)

---

### Post by lsmobrian on 2008-02-01
unzip what you downloaded

in a terminal 

sudo su
cd /path/to/unzipped/folder/
gzip *
cp *.gz /usr/share/man/man1/



hopefully that will work

---

