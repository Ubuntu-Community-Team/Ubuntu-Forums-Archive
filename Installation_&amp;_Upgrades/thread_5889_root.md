---
title: "root"
date: 2004-11-22
forum: Installation &amp; Upgrades
---

### Post by demius on 2004-11-22
hi there. i'd like to know whether it's possible to enable the root account permanently. if so, could someone please tell me how.

Thanks

---

### Post by p!=f on 2004-11-23
[http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root)

I like the root's disabled password. I've found ```
sudo -s
``` (to get a root prompt) to be sufficient.

---

### Post by Malifick on 2004-11-23
:-& 
ok i am having a strange one here with root , i recently installed , got online and checked the faq , and of course it tells me to sudo -s , ok as soon as i do it asks for a password ,i tried just pressing enter , didnt work . ok so tried the next thing sudo passwd root , still asks for a password , i have been at it an hour already triyng different ways to get root , but nothing works,  if there is like a super duper password id appreciate it , or any way to let me get root so i can change the password  and be on with my life 
thanks  :mrgreen:

---

### Post by mr_ed on 2004-11-23
The super duper root sudo password is your regular user password.

---

### Post by LongTooth on 2004-11-23
'sudo -s' seems like a good way to go, security wise. Working with other linux distros I'm well aware of the easy with which one can really foul up one's system. I've done it before -with easy. Working with Ubuntu for some six weeks or so, I've been able to get around my system with no need of a 'root' password. Reading the Wiki on it make me a believer. If I can do all I need without installing a 'root' password, fine and dandy. But I have some questions. I went to the link provided and see this warning:
 
Warning: sudo -s doesn't change the $HOME variable. It can have some bad side effect. You can use sudo -H -s to have a login shell as root.

I haven't the slightest idea what this means. Does this mean that instead of 'sudo -s' I should use 'sudo -H -s'? Can someone clarify? Thanks.

---

### Post by p!=f on 2004-11-23
[QUOTE=LongTooth] 
Warning: sudo -s doesn't change the $HOME variable. It can have some bad side effect. You can use sudo -H -s to have a login shell as root.

I haven't the slightest idea what this means. Does this mean that instead of 'sudo -s' I should use 'sudo -H -s'? Can someone clarify? Thanks.[/QUOTE]

Adding -H parameter means you want to load root's profile completely.
Example:
```

 * 22:58:31 * pef @ agonicus *
[~] > sudo -H -s
root@agonicus:/home/pef # exit

 * 22:59:37 * pef @ agonicus *
[~] > sudo -s

 * 22:59:39 * root @ agonicus *
[~] > cd

 * 22:59:47 * root @ agonicus *
[~] > pwd
/home/pef

 * 22:59:53 * root @ agonicus *
[~] > exit

 * 22:59:55 * pef @ agonicus *
[~] > sudo -H -s
root@agonicus:/home/pef # cd
root@agonicus:~ # pwd
/root
root@agonicus:~ #

```

---

### Post by Malifick on 2004-11-24
mr ed , thank you. for some reason i was confused. i am better now , adios! :mrgreen:

---

### Post by andrel on 2004-11-26
[QUOTE=LongTooth]'sudo -s' seems like a good way to go, security wise. Working with other linux distros I'm well aware of the easy with which one can really foul up one's system. I've done it before -with easy. Working with Ubuntu for some six weeks or so, I've been able to get around my system with no need of a 'root' password. Reading the Wiki on it make me a believer. If I can do all I need without installing a 'root' password, fine and dandy. But I have some questions. I went to the link provided and see this warning:
 
Warning: sudo -s doesn't change the $HOME variable. It can have some bad side effect. You can use sudo -H -s to have a login shell as root.

I haven't the slightest idea what this means. Does this mean that instead of 'sudo -s' I should use 'sudo -H -s'? Can someone clarify? Thanks.[/QUOTE]
 :p 
Merci ,thank you  from french boy. 
A +
andrel

---

