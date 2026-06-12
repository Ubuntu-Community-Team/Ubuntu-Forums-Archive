---
title: "[SOLVED] Mirroring Hardy from a Redhat/CentOS server"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by kai4785 on 2008-06-10
I am trying to build a remote install server that offers as many different distros of linux as possible. I have CentOS and Fedora working wonderfully with a dynamic CGI script that builds my kickstart based on certain parameters. Ubuntu's kickseed project is working swell with the alternate CD. I am having trouble adding software to my installation directory though. What I have done so far:

downloaded the i386 alternate CD.
mounted the CD and copied all the contents into a directory in /var/www/html
copied the correct files into my /tftpboot/pxelinux.cfg directory
copied an example preseed and kickseed (kickstart) script from online tutorials and tested them.

I am able to install a basic system with a few toys like openssh-server and apache2. However, the alternate CD does not have other software like 'mysql' and some php packages I would want to complete a LAMP server install. 

How would I go about mirroring an entire Hardy dist with out mirroring the entire archive, and hopefully with out having to use tools like apt-mirror?

Also, at one point, I would like to have the openssl bugs fixed before first boot, whether done in a post install script, or by updating the package in my installation repository. But that I think I can do on my own with what I learn from getting the other part done first.

-Kai Meyer

---

### Post by kai4785 on 2008-06-13
Problem solved by finding a DVD to download, and unpackaging it in a web accessable location.

---

