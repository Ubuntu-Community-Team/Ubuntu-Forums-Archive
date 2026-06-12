---
title: "How  To Delete .conf file completely after installation"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by sp.mahapatra on 2008-06-11
Hi

can anybody tell me how to delete the conf files after installation of a server

---

### Post by robertchahine on 2008-06-11
try this i think
```

sudo apt-get --purge remove <application>

```

---

### Post by sp.mahapatra on 2008-06-11
thanks,

i tried this command and checked but the files are present and even after restarting the system i m getting the same files.

so what i will do now

---

### Post by Vivaldi Gloria on 2008-06-11
What conf files? Where?

---

### Post by sp.mahapatra on 2008-06-11
i install the apache2 server.
and after installation i changed in the file /etc/apache2/sites-available/default

so now i need to uninstall the apache2 server.
i used the command "apt-get remove --purge apache2"
it shown me it got removed and after that i checked weather the files are present or not but the file /etc/apache2/sites-available/default is present and even after restarting the m/c i m getting the file.

so can u tell me how can i delete these files totally.

Thanks in advance

---

### Post by Vivaldi Gloria on 2008-06-11
> **sp.mahapatra said:**
> i install the apache2 server.
and after installation i changed in the file /etc/apache2/sites-available/default

so now i need to uninstall the apache2 server.
i used the command "apt-get remove --purge apache2"
it shown me it got removed and after that i checked weather the files are present or not but the file /etc/apache2/sites-available/default is present and even after restarting the m/c i m getting the file.

so can u tell me how can i delete these files totally.

Thanks in advance

Type 

```
man rm
```

to learn more about rm before you begin.


When ready give the following commands:

```
cd /etc/apache2/sites-available/
```

Make sure that you are in /etc/apache2/sites-available/ directory by typing

```
pwd
```

Then delete everything there:

```
sudo rm -frv *
```

This will delete everything in that directory and everything in subdirectories, so be careful.

---

### Post by sp.mahapatra on 2008-06-11
There are so many files which got created after the installation of apache2 so how many files i will delete and how can i make take it easy that it is not going to make any problem..

like the files which got created after apache2 got installed is 

/etc/default/apache2
/etc/apache2
/etc/logrotate.d/apache2
/etc/init.d/apache2
/var/log/apache2

so how many files i will delete here

i need a solution

---

### Post by Vivaldi Gloria on 2008-06-11
Ahhh, now I understand your question. You want to know where all the apache related files are and if it is safe to delete these files after you uninstall it. 

I don't know so I can't answer this question. (Actually I thought that --purge would do it).

Anyone?

---

### Post by sp.mahapatra on 2008-06-11
yaa
thats right,i used that one and also apt-get remove <package name>
but it couldn't delete the files.

---

