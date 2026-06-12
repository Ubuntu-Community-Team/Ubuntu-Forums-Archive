---
title: "Samba to Samba migration"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by edwalter on 2007-10-07
Which files need to be copied to the new samba server for the xp pro desktops to stay the same (Not having to rejoin the domain)
I recently installed a new ubuntu server and copied the following files
1. /etc/passwd (only the users portion and added to the new one)
2./etc/groups (only as above)
3.//etc/samba/smbpasswd  (complete)

I setup all the other files as needed and ther server runs great but I had to rejoin all the xp pro machines   
to the domain. This had the nasty concept of changing all the users desktops. I then had to copy all the necessary folders back into the users documents and settings folder.

What files did I miss copying from the older samba server?

Also how do I stop the windows users names to be "USER.DOMAINNAME"

When rejoining the domain this changes to "USER.DOMAINNAME.000"
Thanks for any information or howto guides.
edwalter

---

### Post by edwalter on 2007-10-07
From Me again
I also copied the user portion of the shadow password file
edwalter

---

