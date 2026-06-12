---
title: "Web server"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by xtiano77 on 2010-12-21
A few months ago I set up a LAMP server on my lamp top. Shortly after I removed it and set up Abyss web server. After toying around with Abyss I removed it and set up LAMP back in the same computer; however, I do not know why when I type the address: [http://localhost/](http://localhost/), I get a page that is not the default page for LAMP. I tried removing the LAMP server to see if the page would go away but it does not. The current message showing when I type "localhost" is the following:

It works!
This is the default web page for this server.
The web server software is running but no content has been added, yet.

Now, the only thing I can think of is that while setting up Abyss I had to install PHP on this computer and by mistake I installed both php5-cgi and something else named php-cli or something similar. Can anyone help me figure this out?  Thanks in advance for your help.

HP Pavilion DV6000
Ubuntu 10.10
2GB RAM
Kernel: 2.6.35-24-generic
GNOME 2.32.0
Intel Core Duo T2450 @ 2.00GHz
Available disk space: 116 GB

After doing some research I found out that apache2 is installed in "/etc/apache2" and the root directory is located at "/var/www". I have desktop computer running Ubuntu 10.10 and when I looked on that one I noticed that neither apache2 nor the root directory were present yet LAMP worked just fine. Would it be same for me to remove apache and the root directory from the laptop? Will I need to remove the "php-cgi" and "php-cli" as well?

---

