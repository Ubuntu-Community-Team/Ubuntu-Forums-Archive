---
title: "installing postfix"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by matdavey on 2008-01-31
Many apologies if this has been covered in another post, 

Im currently writing a script that installs postfix automatically and then places the relevant configuration files in /etc/postfix/.

However when the script calls the following command (sudo ) apt-get install postfix this provides me with a problem as the package requires human input to  finish the configuration of the application.  

Does anyone know of any way,  i can install postfix by-passing the need of human intervention to complete the install.

Many thanks for you help.

Mat

---

### Post by kidders on 2008-02-02
Hi there,

There are a few ways of avoiding having to enter a password at that point, such as...
[LIST]
[*]Using expect to type the password for you.
[*]Running the entire script as root.
[*]Reconfiguring the computer not to require a password for "sudo apt-get install postfix".[/LIST]Having said that, all are completely insane, and should never be done.

---

### Post by matdavey on 2008-02-03
Many thanks for your reply, apologies for not being explicit in my original post, however i meant for an automatic way of getting round the postfix configuration screen once the sudo apt-get install postfix command was executed.

Ive managed to unlock the root account when installing ubuntu by using a preseed file and then once all is installed and configured correctly my install script will then lock the root account and reboot.

This allows me to install most applications unattended with exception to postfix and a few others,  which require human intervention to install correctly. But as I have all the configuration files ready to be copied accross i do not require to go through the human configuration process.

---

### Post by matdavey on 2008-02-08
After searching around the interweb a solution for not being greeted with the configuration screen upon installing postfix (and possibly any other packages) is by using  DEBIAN_FRONTEND=noninteractive as either an environment variable or before the command line as follows

DEBIAN_FRONTEND=noninteractive <cmd>

---

