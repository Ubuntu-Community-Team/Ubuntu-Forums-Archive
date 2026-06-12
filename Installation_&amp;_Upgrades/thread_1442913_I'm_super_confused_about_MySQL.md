---
title: "I'm super confused about MySQL"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by ArtemNY on 2010-03-30
Ok after 24 hours of tryings to install MySQL I'm a bit tired. I tried everything. Seems like I've tried every manual searched by Google. No help. I'm STUCK!

So the question is:

[B]1. I currently run 9.10 desktop. What applications or commands should I use to completely uninstall MySQL?

2. How can I check to be 100% sure that there's NOTHING left from old installation. 

[/B][B]3. How can I check that I'm ready to install MySQL, that all permissions are set and I'm good to go?

[/B][B] 4. What applications or commands should I use to install MySQL?

5. How can I check to be 100% sure that this installation completed for 100% and all files are created?

6. I don't want to use some virtualization soft, I want to install it dirrectly to my Ubuntu.[/B]



Oh and one more thing: don't try telling me that I missed something. I surfed all possible info on and off the forum. Nothing helped me to solve the problem!


[SIZE=5][COLOR=Red]**THANK YOU!**[/COLOR][/SIZE]

---

### Post by Barriehie on 2010-03-31
Did you try looking on [http://help.ubuntu.com](http://help.ubuntu.com) ?

---

### Post by ArtemNY on 2010-03-31
> **Barriehie said:**
> Did you try looking on [http://help.ubuntu.com](http://help.ubuntu.com) ?
Used it step by step several times

---

### Post by cavh on 2010-03-31
To uninstall MySQL, type this in a terminal window and then hit the enter key:

```
sudo apt-get remove mysql-server
```

and then, to make sure, search for mysql in Synaptic (get there by going System -> Administration -> Synaptic then type *mysql* in the search box) and see if any mysql-related entries have a green-filled tick box. If they do, right-click the green box and select 'mark for complete removal'. Once you have right-clicked all the green boxes you need to, then click on the big green apply tick logo at the top middle of the Synaptic window. This should completely remove mysql.

I would then suggest installing a LAMP server (LAMP stands for Linux, Apache, MySQL and PHP) using the tasksel command in a terminal: just type ```
tasksel
``` in the terminal window and hit enter. Once you have done this, if you want to use phpMyAdmin to administer the MySQL installation, type this into a terminal:
```

sudo apt-get update
``` (this will refresh the list of software packages available for download)

and then type

```
sudo apt-get install phpmyadmin
```

Doing the LAMP install using tasksel is super easy;)

---

### Post by ArtemNY on 2010-03-31
> **cavh said:**
> To uninstall MySQL, type this in a terminal window and then hit the enter key:

```
sudo apt-get remove mysql-server
```and then, to make sure, search for mysql in Synaptic (get there by going System -> Administration -> Synaptic then type *mysql* in the search box) and see if any mysql-related entries have a green-filled tick box. If they do, right-click the green box and select 'mark for complete removal'. Once you have right-clicked all the green boxes you need to, then click on the big green apply tick logo at the top middle of the Synaptic window. This should completely remove mysql.

I would then suggest installing a LAMP server (LAMP stands for Linux, Apache, MySQL and PHP) using the tasksel command in a terminal: just type ```
tasksel
``` in the terminal window and hit enter. Once you have done this, if you want to use phpMyAdmin to administer the MySQL installation, type this into a terminal:
```

sudo apt-get update
``` (this will refresh the list of software packages available for download)

and then type

```
sudo apt-get install phpmyadmin
```Doing the LAMP install using tasksel is super easy;)

The problem is that I did all that. I've read official docs several times. Googled and Ubunted all possible info - no help. I'm starting thinking that there's ether broken copy of Ubuntu CD or my PC doesn't want to work with 32-bit Ubuntu. I'm running 64-bit core. 

Downloaded and installed 64-bit Ubuntu, let's see if it fix the problem.

---

### Post by ArtemNY on 2010-03-31
No, the problem is not fixed on 64-bit.

I just don't understand how it can be possible.

---

### Post by cavh on 2010-04-01
Are you able to run the mysql command at all, from a terminal? Try

```
mysql -u root -p
```

in a terminal and then enter the password you chose, to see whether mysql is currently installed.

You can also do a search from the root drectory to see what mysql folders and files still exist on the system

```
sudo find / -name mysql -type d
```
for directories

and 

```
sudo find / -name mysql -type f
```
for files

---

### Post by ArtemNY on 2010-04-01
**[SOLVED]**


When I was trying to install first several times, I used 32-bit Ubuntu, and it refused to work correctly with my 64-bii core or it had too many bugs because the updates were running with mistakes, terminal was running with mistakes and some more application were running with mistakes even after several re-installations of OS.

When I finally installed 64-bit. Everything were fixed. No mistakes in no applications.
However the LAMP still couldn't be installed and the problem was in an official documentation mistakes. In some general LAMP installation steps and in some apache and mysql steps. When I finish everything, I'll make another thread about it, hope it'll be fixed for another newbies like myself. :)

---

