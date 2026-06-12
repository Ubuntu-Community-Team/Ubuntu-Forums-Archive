---
title: "update partly fails due to dependency problems"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by roythomas on 2007-08-13
Hi All. 

I have just installed a fresh copy of Ubuntu 7.04 and all went well. But when I did the update some of it failed due to dependency issues. The problem is that the updater doesn't think anything went wrong so doesn't offer to reinstall anything. The Update Manager thinks the “system is up to date”.

How can I deal with this? Is it a problem?

Thanks, Roy

---

### Post by bapoumba on 2007-08-13
Did you have any particular error message? Its going to be difficult to help you without knowing. Which packageis giving you errors?

You can also post your sources.list. Open a terminal (Accessories > Terminal) and paste the complete output to:
```
cat /etc/apt/sources.list
```
Do you have any error message to:
```
sudo aptitude update
```

---

### Post by PaulFr on 2007-08-13
I would suggest you run in a terminal```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```and see if there are any errors.

---

