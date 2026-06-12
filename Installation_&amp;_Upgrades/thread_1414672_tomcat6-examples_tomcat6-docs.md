---
title: "tomcat6-examples tomcat6-docs"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by ptdecker on 2010-02-23
I successfully ran 'sudo apt-get install tomcat6-examples tomcat6-docs' and it looks like the installer put each under directories in /usr/share.

But, when I go to the default tomcat welcome screen at [http://localhost:8080](http://localhost:8080) and try to follow the related links to the docs and examples on the page, I receive 404 errors.

I noticed that tomcat is going to /var/lib/tomcat6/webapps/ROOT/ for the default index page, so I'm assuming that it is looking in /var/lib/tomcat/webapps for /doc and /examples instead of where they were installed in /usr/share.

Help?!?   What do I need to do to get /doc and /examples where they need to go and properly installed?

Sorry in advance for the n00b question.

P. Todd Decker

---

### Post by bruno9779 on 2010-02-23
a symbolic link. 

ln -l ...

for the exact command you need more info (exact name of files or folders and the location they are supposed to be)

---

