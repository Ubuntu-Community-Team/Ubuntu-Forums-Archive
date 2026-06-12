---
title: "Trouble seeing .php pages on remote LAMP server"
date: 2014-09-23
forum: Installation &amp; Upgrades
---

### Post by rlntel on 2014-09-23
I've previously installed LAMP on virtual servers on the same machine where I'm writing php, but I had a couple of unused laptops so this time I thought I'd install LAMP on those to create an environment at home that more closely resembles conditions at work.

[SIZE=2]*(First...the laptops I'd already installed with 14.04. Should those have been installed with a server version of Ubuntu instead? If so, which do you recommend?)*[/SIZE]

My primary issue is...after installing LAMP on either of these remote servers, I can reach Apache at /var/www/html with 192.168.1.[#]. However, if I touch a test.php page to the same directory and try to reach 192.168.1.[#]/test.php, I get nothing. Why?

This problem doesn't happen when LAMP is installed on the virtual server, so I'm a little lost.

Thanks in advance.

---

### Post by tgalati4 on 2014-09-23
Check the root web page directory definitions for both apache and php in your configuration files.  Compare them between the laptop and the virtual instances.  How you installed LAMP will affect the default configuration.  Was there a difference in the installation procedure between the two environments?

Check the permissions and ownership of the /var/www directories between the two environments.

---

