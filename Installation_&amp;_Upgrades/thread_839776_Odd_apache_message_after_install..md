---
title: "Odd apache message after install."
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by YourSurrogateGod on 2008-06-24
Ok, so I went here in order to set up my box for some web development.

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Internet_and_Web_Development](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Internet_and_Web_Development)

Everything went nice and smooth until I got to this part:
```
sudo /etc/init.d/apache2 restart
```

I got this message:
```
$ sudo /etc/init.d/apache2 start
 * Starting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                          [ OK ]
```
... and I have no idea what the problem might be.

Also, I can go to my localhost and see a message It works! displayed, but when I do [http://localhost/phpmyadmin](http://localhost/phpmyadmin), I get a "The requested URL /phpmyadmin was not found on this server." message.

I'll admit that I'm newbish to PHP and Apache and I'm not sure what I should do next. I re-checked my steps to make sure I didn't skip anything, but no go. Thoughts?

---

