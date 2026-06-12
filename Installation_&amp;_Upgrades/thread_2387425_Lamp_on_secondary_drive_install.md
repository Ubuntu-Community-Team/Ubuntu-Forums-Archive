---
title: "Lamp on secondary drive install"
date: 2018-03-19
forum: Installation &amp; Upgrades
---

### Post by aitkenrob on 2018-03-19
When I installed lamp on my primary drive, I needed to insert my password every time I saved to /var. Can I install it on my secondary drive so I dont have password permission issues?

---

### Post by yancek on 2018-03-19
Installing LAMP on a secondary drive won't resolve that issue.  You need to change ownership/permissions on the sub-directories under /var/www/html.

---

### Post by TheFu on 2018-03-19
No.  That would break system security and almost all the programs.  

You can setup a longer timeout for sudo use, however.

Understanding Unix file and directory permissions is a core skill for anyone using a Linux machine. There are many tutorials.

---

### Post by SeijiSensei on 2018-03-19
You can store the website files anywhere on the server.  You just need to change the "DocumentRoot" directive in Apache.  For example, suppose I've created a folder in my home directory called /home/seiji/web and put my various .html and .php files there.  Then in Apache, I could create a virtual server with the directives

```

<VirtualHost *:80>
ServerName      www.example.com
DocumentRoot    /home/seiji/web
[etc.]
</VirtualHost>

```

---

