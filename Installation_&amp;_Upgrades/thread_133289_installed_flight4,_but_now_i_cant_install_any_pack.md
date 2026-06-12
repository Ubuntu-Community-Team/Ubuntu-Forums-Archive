---
title: "installed flight4, but now i cant install any packages?"
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by bbqbaker on 2006-02-19
when i try to install mysql, ruby, and some other things, i get these this following msg: is there any way around this? do i need to recompile something? thx.

poipu@ubuntu1:~$ sudo apt-get install rails irb libdbm-ruby1.8
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  irb: Depends: irb1.8 but it is not going to be installed
  rails: Depends: rdoc (> 1.8.2) but it is not going to be installed
E: Broken packages
poipu@ubuntu1:~$

---

### Post by jjross on 2006-02-19
have you checked to make sure you have all the repositiries, usually when you first install all the repo's are not set up

---

### Post by bbqbaker on 2006-02-19
if you mean the sources.list file, i am using the same one for ubuntu 5.10.....unless does flight4 have its own seperate sources.list?


what is the difference between the 2?

---

### Post by jjross on 2006-02-19
let me look around for a few minutes and i'll find a link for you to go 
ok try this link, it may answer some questions for you, just remember it needs to say dapper instead of breezy
in the repo address

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)
 here is one more

[http://ubuntuforums.org/showthread.php?t=127202&highlight=repositories](http://ubuntuforums.org/showthread.php?t=127202&highlight=repositories)

---

