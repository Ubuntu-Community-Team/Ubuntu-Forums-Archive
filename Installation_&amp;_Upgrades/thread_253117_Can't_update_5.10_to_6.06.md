---
title: "Can't update 5.10 to 6.06"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by Tominator on 2006-09-07
Have tried several times to update using update manager. I get the following error message. Failed to Fetch [http://security.ubuntu,com/ubuntu/dists/breezy-security/Release](http://security.ubuntu,com/ubuntu/dists/breezy-security/Release) Unable to find expected entry deb/binary-i386/packages in Meta-Index file (malformed Release file?) That is the message, Am I doing something wrong or is there another way to accomplish the upgrade? Thanks, Tom

---

### Post by croak77 on 2006-09-07
1. You need to change all the breezy to dapper in /etc/apt/sources.list

2. In that url, you have a ',' instead of a '.' in security.ubuntu,com

3. Read this: [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

---

### Post by Tominator on 2006-09-08
OK, Thanks very much for the info Croak. I'll read up and try to do as the article suggests.

---

### Post by Tominator on 2006-09-08
One more question. After reading the article it says make sure I have the ubuntu or kunbutu desktop. I believe I have the gnome desktop. Is it the same thing? If  not what must I do about that. Thanks again.

---

