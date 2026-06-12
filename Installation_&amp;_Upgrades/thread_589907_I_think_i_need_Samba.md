---
title: "I think i need Samba"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by williamburn on 2007-10-24
So i have a Feisty box setup and working nicely with Apache2, MYSQL5, and Webmin.  So far so good.  I virtualized a few webs and they open great in my windows environment.  however, one thing occured to me.  How will my developer transfer files between the windows world and linux world?  

For the administration i have been using ssh and am able to quickly login from anywhere on my network.  my question is, how can i move files, easily, or how can i recognize my new linux webserver as a file share?

I am still pretty new to this linux thing and if there is a best practice can you please enlighten me.

Thank you very much

---

### Post by pjhsv on 2007-10-25
Most common way is via ftp.  I wouldn't be allowing samba shares accessible over the internet, that's a pretty serious security risk.

For copying within your network though, and being able to mount a network drive on a windows machine, yes, you'll want to install samba server.

---

### Post by oregonbob on 2007-10-25
You need sftp - ftp over ssh, port 22. On wondows get FileZilla, on linux its 'sftp' command.

---

