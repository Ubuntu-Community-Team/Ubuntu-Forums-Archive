---
title: "cannot use application that require root access"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by relentles on 2005-06-19
i installed ubuntu a while ago. i have no problem booting up etc and logging in and using some of the function like root terminal, networking etc etc. i was able to shutdown and boot up and still i was able to use those functions

then, the last time i shutdown and went to sleep and the next time i on my laptop again, i was not able to use those functions again, they will start and then disappear. I wasn't able to even log on to the internet, to do so i have to su, do a manual config on my wireless card b4 i was able to go online

i have checked my /etc/sudoers and the below lines are as follow
  GNU nano 1.2.4               File: /etc/sudoers.tmp


# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

i have also tried adding my username to the group admin
and all i get was it telling me tat i am already in the group admin
note tat i cannot use any function tat requires root access, including changing the user access type or grp access type. the only way i can do anything tat requires root access is to do it thru the terminal. Note that i cannot use root terminal however i can open terminal and su from there

please advice

---

### Post by afonic on 2005-06-19
Just use sudo instead of su.

Read the FAQs...

---

### Post by relentles on 2005-06-19
i further found tat the problem could be due to the terminal. the command to run each of those short cuts in system is gksudo users-admin, gksudo network-admin etc, they always start with **gksudo.**
i am able to run them in the terminal, however, i am not able to run them as shortcuts unless they are run in terminals. 
is there a way around getting them to run not from the terminals, and allows them to just run in the background?

---

### Post by relentles on 2005-06-20
[QUOTE=afonic]Just use sudo instead of su.

Read the FAQs...[/QUOTE]
i have read the faq and they do not seems to have wat i wanted.
i do not want to log in as root. i just want to be able to do the admin stuff without going through so much hassle. i mean the icons are there, but i am just not able to use it.

realised tat whenever i run from the terminal i received the following
jianhui@:~$ sudo network-admin
sudo: unable to lookup  via gethostbyname()

could this have been causing the error?

---

