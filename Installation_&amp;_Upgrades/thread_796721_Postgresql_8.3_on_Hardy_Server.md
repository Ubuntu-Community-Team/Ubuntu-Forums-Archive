---
title: "Postgresql 8.3 on Hardy Server"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by AndEat on 2008-05-16
Hi, 

I am installing Postgresql latest package on Hardy Server 

*can anyone suggest a clear and concise how-to or tutorial on setup?*

---

### Post by ibutho on 2008-05-16
I don't think you need a specific howto for that. You can install postgresql and postgresql-client using the packaging tools and you should be good to go.

---

### Post by AndEat on 2008-05-16
I have tried that and have run into a few roadblocks....

- things like initdb and postgres are not installed 

- starting  /etc/.../postgresql-8.3 start results in no response or any log entries I can find so I'm a bit perplexed and thinking I missed a step or two  somewhere, anyone's perspective appreciated

---

### Post by AndEat on 2008-05-16
i've found this useful:

[http://hocuspokus.net/2008/05/13/install-postgresql-on-ubuntu-804/](http://hocuspokus.net/2008/05/13/install-postgresql-on-ubuntu-804/)

I've had no problems installing locally, but think something went awry on the  server I was working on, the install wasn't quite right.

---

### Post by ssavelan on 2008-09-11
> **AndEat said:**
> I have tried that and have run into a few roadblocks....

- things like initdb and postgres are not installed 

- starting  /etc/.../postgresql-8.3 start results in no response or any log entries I can find so I'm a bit perplexed and thinking I missed a step or two  somewhere, anyone's perspective appreciated

I am going through the same 9-11-08... I couldn't get the source to work correctly with all the path and bash issues... I spent a few hours with INSTALL... now I am going back to the package manager.. experiencing the same problems you describe with paths and passwords....

---

