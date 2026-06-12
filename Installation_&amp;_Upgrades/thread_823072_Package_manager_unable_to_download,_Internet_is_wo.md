---
title: "Package manager unable to download, Internet is working"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by jackson_vkh on 2008-06-08
Hi!

My internet connection is working fine.  However every time I try to update or install something I get a message saying:

Could not download all required files  Please check your internet connection or installation medium.

Any ideas?

---

### Post by Pumalite on 2008-06-08
sudo apt-get --configure -a
Post the output

---

### Post by jackson_vkh on 2008-06-08
jason@homebench:~$ sudo apt-get --configure -a
E: Command line option --configure is not understood
jason@homebench:~$ sudo apt-get -configure -a
E: Opening configuration file onfigure - ifstream::ifstream (2 No such file or directory)

---

### Post by Pumalite on 2008-06-08
Sorry.
sudo dpkg --configure -a

---

### Post by jackson_vkh on 2008-06-09
Thanks for the quick replies.  It turns out my problem was the Canadian mirror is down.  I switched over to the main repository and Bob's your unlce.  Thanks for the help!

---

