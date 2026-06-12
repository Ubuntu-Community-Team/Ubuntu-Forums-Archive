---
title: "Where are files of Ubuntu 6.10 Edgy Eft"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by ctomczyk on 2008-05-31
Hello.

Today I have just try to upgrade my Ubuntu 6.10 Edgy Eft, but I had message that files doesn't exists. For example:

[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz)
404 Not Found

So, how can I upgrade my Ubuntu to newer version? Where is distribution files for 6.10 Edgy Eft?

-- 
Best regards,
Cezary

---

### Post by sisco311 on 2008-05-31
[http://www.ubuntu.com/news/ubuntu610end-of-life](http://www.ubuntu.com/news/ubuntu610end-of-life)

---

### Post by ctomczyk on 2008-05-31
So, there is only one option: remove 6.10 and install newer version?

-- 
Cezary

---

### Post by ctomczyk on 2008-05-31
Well, I try use:
sudo sed -e ’s/\edgy/feisty/g’ -i /etc/apt/sources.list

and then upgrade using standard upgrade manager. Maybe will be good. We'll see.

-- 
Cezary

---

