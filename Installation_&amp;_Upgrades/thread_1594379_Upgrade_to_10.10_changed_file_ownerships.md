---
title: "Upgrade to 10.10 changed file ownerships"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by leupi on 2010-10-12
I have Tomcat installed on Ubuntu and just upgraded from Ubuntu 10.04 to 10.10. I then noticed that every file in my tomcat6 directory was now owned my tomcat6 and the group was also tomcat6. I believe that the permissions were rwx-rwx-x meaning that I could no longer modify any of my webpages. If I created a page Tomcat said that the file did not exist (I neglected to see what those file permission were). I did a chwon -R to give myself ownership of all of the files and then a chmod -R 755 so that TC could then read and display them.

I found it strange that upgrading Ubuntu would change the ownership of those files but I can't remember anything that I did beside that that would have done so. Any thoughts?

---

