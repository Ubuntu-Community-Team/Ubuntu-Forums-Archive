---
title: "Help with samba install"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by Alpha_omega16 on 2006-08-23
I have the ubuntu lamp server installed and i am trying to install samba 3.0.23b. i have the file unzipped when i go to configure it i get an error 
"configure: error: no acceptable C compiler found in $PATH See 'config.log' for more details."
I am new to Ubuntu so any help you could give would be great.

Jason

---

### Post by VirtuAlex on 2006-08-23
install build-essentials package if you want to compile, but is there any really good reason why you are not using samba from repos?

---

### Post by Alpha_omega16 on 2006-08-23
Well i was unaware of samba from repos. where would i get it?

---

### Post by VirtuAlex on 2006-08-23
sudo apt-get install samba
and if you want to search repositories
apt-cache search packagename

---

### Post by Alpha_omega16 on 2006-08-23
it worked. Thanks for the help.

---

