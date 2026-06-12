---
title: "HOWTO: Installing Apache"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by shlic on 2006-08-16
Can anyone tell me, step by step how to install Apache? I have linux Kubuntu 6.06. I tried many things, search over net, but everything i try just wont work. When i install apache and want to connect to localhost in my web browser, nothing, and after 80sec, i get message timeout expired. I tried to edit conf files like people suggest over net, but nothing. 
TNX. Sorry about my english, i am from Croatia.

---

### Post by tseliot on 2006-08-16
You shouldn't ask questions in the HOWTOs, Tips & Tricks section.

I'm moving this thread.

---

### Post by shlic on 2006-08-17
Nobody knows how????

---

### Post by denday on 2006-08-17
Have you try :

```
sudo apt-get install apache
```

---

### Post by shlic on 2006-08-19
Ive tried this:
1) Installing over adept
2) Installing over sudo apt ......
3) I try to install apache 1.3 and apache2
4) I search over the net, and try somethings, like editing 
   httpd.conf or when you install apache2 the apache2.conf

And i tried this things and always the sam thing, i try to connect to localhost and nothing. So was anyone had this problem or not? I don`t know what to do more.

---

### Post by devnulljp on 2006-10-14
> **shlic said:**
> Ive tried this:
1) Installing over adept
2) Installing over sudo apt ......
3) I try to install apache 1.3 and apache2
4) I search over the net, and try somethings, like editing 
   httpd.conf or when you install apache2 the apache2.conf

And i tried this things and always the sam thing, i try to connect to localhost and nothing. So was anyone had this problem or not? I don`t know what to do more.

Which of those didn't work? 
What errors/problems? 
What types of tests?
What edits to httpd.conf/apache2.conf?

You should be able to install with 
```
sudo apt-get install apache2
```
Then you'll need to set it up...is that where you're having problems? 
Try: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) to get you started

Let me know if that helped

---

### Post by lawahdy on 2007-08-24
> **devnulljp said:**
> 
Then you'll need to set it up...is that where you're having problems? 
Try: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) to get you started

Let me know if that helped

thanks a lot man.. great link.. I'm sure this is what he wanted.. anyways this link  provides all the answers for the dude.. whether he wants to install or configure.. 

it helped me configure for sure.

thanks again.

---

### Post by tc101 on 2007-10-31
Here are the instructions for 7.10  Gutsy:

[http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html)

---

