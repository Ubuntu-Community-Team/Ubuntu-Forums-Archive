---
title: "installing wordpress into my domain"
date: 2023-06-29
forum: Installation &amp; Upgrades
---

### Post by steveact on 2023-06-29
i have some questions 

i have an transIP website domain with an perfomance ubuntu vps from transIP. I've configured the domain with my vps and i want to install wordpress on my domain, but i am not sure how. ive tried to follow the wordpress installation tutorial but no success. even the localhost website i made with the tutorial does not work how i wanted it to work. Any ideas?

link installation tutorial here
[https://ubuntu.com/tutorials/install-and-configure-wordpress#1-overview](https://ubuntu.com/tutorials/install-and-configure-wordpress#1-overview)

---

### Post by mIk3_08 on 2023-06-29
You have lot to learn for this not just entering those commands. know first your "root" "ssh" and etc. Set-up is very easy when you know exactly where you are. Know the basic first which is "root Home(with your Static IP)". I'm not too good at this but I am pretty sure when I'm in your side I can easily handle the situation. Not too easy but I'm sure I can. Regards and cheers.

---

### Post by ActionParsnip on 2023-06-29
[https://www.digitalocean.com/community/tutorials/install-wordpress-on-ubuntu](https://www.digitalocean.com/community/tutorials/install-wordpress-on-ubuntu)

I always suggest Digital Ocean

---

### Post by SeijiSensei on 2023-06-29
You unpack the wordpress ZIP file into a directory which you make available via Apache or some other server. On Ubuntu, the default website directory is /var/www/html. You should see the default index.html page in this directory if you connect to your server with a browser.

If you've never used SSH and shell commands, this is likely to be a long process. First find articles that talk about how to set up a web server with "LAMP" (Linux-Apache-MySQL-PHP) and get a simple site up and running. As a first start, I suggest creating a file called "index.php" in the default directory with simply the line

```
<?php phpinfo() ?>
```

then view it from a browser. What do you see?

---

