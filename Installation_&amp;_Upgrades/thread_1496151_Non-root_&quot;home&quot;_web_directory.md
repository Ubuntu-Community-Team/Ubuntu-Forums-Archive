---
title: "Non-root &quot;home&quot; web directory?"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by olwe on 2010-05-28
I'm trying to install Wordpress on my home machine running Ubuntu 10.04. I've got LAMP successfully set up per apt-get. Wordpress should be in the "web directory," but this appears to be /var/www/
which is root/root. I don't want to become root and move the wordpress bundle into /var/www/ I'd rather set up a directory in my home folder for my web tinkering and have LAMP see and interact with it there, like /home/myhome/www/wordpress/ Is this just setting up a symbolic link? Or is it trickier? I'll take my answer off-line...

---

### Post by olwe on 2010-05-29
I went to the /var/www/ directory and created a symbolic link:

```
ln -s /home/myhome/blog blog
```

and that seems to work, although the permissions on the link are lrwxrwxrwx root root, which might not be what I want. My box has a dynamic IP address (randomly assigned), so I'm not so worried about outsiders coming in, but what should the permissions be on my symbolic link?

Also, somebody suggested using per-user web directories:
 [httpd.apache.org/docs/2.0/howto/public_html.html]("http://httpd.apache.org/docs/2.0/howto/public_html.html")

---

