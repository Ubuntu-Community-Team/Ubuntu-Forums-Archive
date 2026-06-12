---
title: "Broken Links of BitTornado"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by cgabilla on 2007-07-17
Hello, I am new to Ubunto.

I installed Automatix and run it successfuly.

Using Automatix, I installed File Sharing application called BitTornado, but it was unsuccessful. It says that there are broken files.

As it suggested to run Synaptic, I did it but it won't install the downloaded broken files.

I want to un install this thing BitTornado because it really pissed my off. My package manager will not run because of this broken files.

Anyone could help me?

As I run apt-get also, it says:

cyrus@cyrus-desktop:~$ sudo apt-get check
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libwxgtk2.6-0: Depends: libwxbase2.6-0 (>= 2.6.3.2.1.5ubuntu6) but it is not installed
  python-wxgtk2.6: Depends: libwxbase2.6-0 (>= 2.6.3.2.1.5ubuntu6) but it is not installed
E: Unmet dependencies. Try using -f.

How do I fix this dependency? Or How can I get them away from my computer (the errors, BitTornado).

Thanks for the answers in advance.

Have a nice day.

---

### Post by doogy2004 on 2007-07-17
Please forward this to the automatix forums at [www.getautomatix.com/forum/](www.getautomatix.com/forum/)

---

### Post by Hallvor on 2007-07-18
Did you try

> sudo apt-get -f install?

---

