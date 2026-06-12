---
title: "Can't install phpmyadmin"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by jfurfey on 2006-09-13
Just installed 6.06 lamp server.   Everything went fine.

However phpmyadmin won't install.

Trying, sudo apt-get install phpmyadmin

It gives me, E:  couldn't find package phpmyadmin

Any ideas?

---

### Post by Jagot on 2006-09-13
phpmyadmin is in the universe repository which is not enabled by default.  See here to do so:

[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)

---

### Post by jfurfey on 2006-09-13
Thanks, that did the trick.

I did have to run 'sudo apt-get update' before it would find the package though.

Take care.

---

### Post by johnward on 2006-10-25
Excellent, I was having the same trouble and this solved my problem

---

### Post by arst06d on 2006-10-26
Hi

I too want to install phpmyadmin, so need to enable the universe repository.  Having trouble, however.

Connecting using winscp from xp box, I open the file to edit but when I save I get a permission denied.

How do I edit from the command line of a LAMP server?  I've had a look at vi but it is not intuitive at all ...

Thanks

---

### Post by FyreBrand on 2006-10-26
Follow this guide carefully: [**HowTo: Install Apache-MySql-PHP**]("https://help.ubuntu.com/community/ApacheMySQLPHP?").

This will ensure you have all the packages you need to install and all of the configuration you need to perform especially the critical root admin setup.  Read it carefully. It's a very good and simple guide and has helped me perform this install successfully several times.

On a side note if you're not comfortable with VIM (and you're right it's not intuitive) then try "nano" (no quotes).  It is also a command line editor but a lot easier and more intuitive to use.  So where you see:
```
vim /foo-path/foo.file
```
substitute
```
nano /foo-path/foo.file
```It has a list of important commands at the bottom of the editor such as save and exit.

---

### Post by arst06d on 2006-10-26
Thanks for that info
In the meantime, I'd found a cheat-sheet for vim [here]("http://www.nuclearblender.com/leftovers/howto/vim/vimcheat.html").
Then did 
sudo apt-get update
sudo apt get install phpmyadmin

Now I can use phpmyadmin from firefox on my xp box via //myipaddress/phpmyadmin/.

Many thanks

---

