---
title: "FTP/Web permissions"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by tbresson on 2006-08-30
My current setup is an Apache2 webserver and a VSFTPd FTP server.

My first issue was to get access to the /var/www dir from my ftp user. I managed that by enabling system users in VSFTPd and not ch-jailing them, doing a symlink with ln -s, and changed the ownership of the www dir to my admin user.

While this does give me access to my www dir it still prevents me from uploading data to my web because the uploaded files' permissions are not set so a regular web-surfer can see the file, I have no manually logon with SSH and do a chown -R on it to get it to work. 

I need help being able to upload a file into my www dir and when done the file will have the permissions needed for viewing on my apache.

---

### Post by tbresson on 2006-09-05
* bump *

---

### Post by Original Brownster on 2006-09-05
Hi,
I had to do this a while back but on debian / redhat box's.
find the name of the user process who runs the web service, use ps -aux and look for the process and user name for the apache web server.
set the initial group of your admin user to this group, either using usermod or the user admin gui tool.
new files created by this user will have owner as admin and group as the web-server user. AFAIKR the default permissions for the group will be readable and therefore should work.
Otherwise you can change the default file creation permission attributes for a user.

[This article]("http://www.linuxforums.org/security/file_permissions.html") explains it well.

---

### Post by tbresson on 2006-09-06
Thank you.

I'll look into it :)

---

