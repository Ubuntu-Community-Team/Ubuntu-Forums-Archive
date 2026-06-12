---
title: "Need help to setup LAMP, minecraft, FTP etc."
date: 2011-11-22
forum: Installation &amp; Upgrades
---

### Post by fidde88pven on 2011-11-22
Hi!

Once again Im going nuts trying to install a server in my home...

I now use ubuntu (Ive tried mint and fedora aswell).
Well I have so many problems I cant write them all, instead I right what I need to setup, and then I hope you can help...?

- Free server in my house
- McMyAdmin
- PHP5 (apache2)
- Webmin or equal control panel to admin over web
- Remote desktop
- PhpMyAdmin
- FTP (or better) access to the www folder
- Ability to add and delete users for the above
- Samba share for local network

Best distro? Easiest way? Most secure?
Any ideas?

Thanks anyway!
Best regards

---

### Post by Lars Noodén on 2011-11-22
Ubuntu server will do the job just fine.  Instead of Webmin, try to learn to manage you server via the shell. Webmin is a crutch and ok for assistants but if the web server is down, so is webmin.  The main sysadmin needs to be able to go in and work on the server even when the web server is unavailable.

Also, it's time to [stop using FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/) and use SFTP instead.  It's already part of OpenSSH server so if you have SSH available, you already have SFTP configured and running.

---

### Post by Lars Noodén on 2011-11-22
You can add or delete users with [adduser](http://manpages.ubuntu.com/manpages/precise/en/man8/adduser.8.html) and deluser.

---

### Post by fidde88pven on 2011-11-22
Okay! That sounds ok...

But how do I change so that a user ONLY can access www-folder?

---

### Post by fidde88pven on 2011-11-23
No one? Its very important, and I dont understand OpenSSH...

Suggestions, alternatives?

---

