---
title: "Issue with Proftpd"
date: 2015-04-18
forum: Installation &amp; Upgrades
---

### Post by Mike_Hughes on 2015-04-18
I am using Dreamweaver to try and put my site back on the new server. I tested the ftp connection once configured and it said it worked. When I try and put a file up I get the following error. 

tarted: 4/18/15 17:59

Path was: /var/www/mikealrhughes.com/public_html/MM_CASETEST4291
Path was: /var/www/mikealrhughes.com/public_html/mm_casetest4291
Path was: /var/www/mikealrhughes.com/public_html/MM_CASETEST4291
Connected to mikealrhughes.com.
Path was: /var/www/mikealrhughes.com/public_html/_mm
Path was: /var/www/mikealrhughes.com/public_html/_mm
Path was: /var/www/mikealrhughes.com/public_html/index.html
index.html - error occurred - An FTP error occurred - cannot put index.html.  Access denied.  The file may not exist, or there could be a permission problem.   Make sure you have proper authorization on the server and the server is properly configured.

File activity incomplete. 1 file(s) or folder(s) were not completed.

Files with errors: 1
index.html

Finished: 4/18/15 17:59

I thought I had permission on the server to put files on it. How do I check permission for user macmike?

---

### Post by Mike_Hughes on 2015-04-18
I did get the permission solved. I didn't like having to open them up to all users but since I am the only user now be ok. I tried chmod -R 700 and 711 neither let me upload files.

---

