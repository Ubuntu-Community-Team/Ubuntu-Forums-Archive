---
title: "Apache Config ( Newbie )"
date: 2022-07-28
forum: Installation &amp; Upgrades
---

### Post by sidknee on 2022-07-28
Hello all :~)
I have just installed apache, but want to have my Root DIR in a different place to install , ie Not /var/www/ .
I am using Vim , but cannot seem to be able to edit the config file. ( I am coming from IIS ) .
Also , I have put Multiple IP's on the box & would like to run different Websites on Each, is that in the Hosts file ?
Sorry if I am wasting your time.
Cheers
Sid

---

### Post by yancek on 2022-07-29
Which release of Ubuntu are you using?  The link below explains installing/configuring on 22.04.  The configuration files on Ubuntu are in /etc/apache2 and the primary configuration file is apache2.conf.. There are quite a number of sites explaining this online so if you don't understand fully the explanation at the link below just do an online search for installing apache2 on Ubuntu (version number).

[https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-22-04)

---

### Post by ActionParsnip on 2022-07-29
To edit the files you will need to prefix the vim command with "sudo". As with all text files, make a backup of the existing file before editting

---

### Post by sidknee on 2022-07-30
Thank-You Both.
I will do as you suggest.
Cheers
S

---

