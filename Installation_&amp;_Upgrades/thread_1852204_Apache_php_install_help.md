---
title: "Apache php install help"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by moonguide on 2011-09-29
I have Apache, php, and MySQL running on my desktop machine on Ubuntu 10.04. I recently upgraded my laptop and am running 10.04 on it, too. I'm trying to duplicate most of what is on the desktop machine on the laptop. I used Synaptic on my laptop and installed all the Apache and php packages that are marked in Synaptic on my desktop. Apache started up with the "It works" index.html page. When I replaced it with index.php and navigate to localhost I get a window titled "Opening" that asks, "What should Firefox do with this file?"

I tried restarting Apache but it didn't change anything. I also tried reloading apache, mysql, and php with aptitude and, after restarting apache, still saw the same dialog.

What did I miss in my installations?

Thanks.

---

### Post by judoka9999 on 2011-09-29
I'm not sure if this will still apply on 10.04, as I'm not sure if that is Apache2, but perhaps try:

sudo a2emod php5
sudo /etc/init.d/apache2 restart

---

### Post by moonguide on 2011-09-30
> **judoka9999 said:**
> I'm not sure if this will still apply on 10.04, as I'm not sure if that is Apache2, but perhaps try:

sudo a2emod php5
sudo /etc/init.d/apache2 restart

sudo: a2emod: command not found

Thanks for the idea, but it didn't work.

---

### Post by Dangertux on 2011-10-01
Try 

```

a2enmod

```

With that command instead, should work then or at least tell you it's already installed.

---

