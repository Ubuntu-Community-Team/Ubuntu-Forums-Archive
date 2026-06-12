---
title: "Are these steps correct for 7.10 installation?"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by herbnet on 2007-10-28
Are the steps in preparing Ubuntu to receive OSC go like this via the root user account:
1. sudo apt-get install apache2 
2. sudo apt-get install php5-mysql 
3. sudo apt-get install libapache2-mod-php5
4. sudo apt-get install mysql-server
5. sudo apt-get install phpmyadmin and reconfigured for apache2 

Determined the IP-address using ifconfig and the inet addr value of the "Link encap:Ethernet" block

The command `mysql status` returned ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

netstat -tap shows mysqld and apache2 and cupsd with a status of LISTEN 
++++++++++++++++++++++++++++++++++++++++++++++++
So here is where I stand in my installation. What do I need to correct the error and/or what did I do or not do to cause it?

What are the next steps after the correction(s)?

---

### Post by herbnet on 2007-10-28
After playing around for the last hour have come across thiese things:

First try this: mysqladmin status
You should get the error you were getting before. During the mysql-server installation you should've been asked to set a password for root. If you did not when the prompt "Enter password:" shows up hit the enter key. If you entered a password during the mysql-server installation, enter that password at the "Enter password:" prompt. So let's see what happen now with adding a parameter to the command you first tried.

mysqladmin -p status
Oaky you should see the "Enter password:" prompt. After following the instructions above you should see a report back on how mysql is running. Replace status with ping, which should return "mysql is alive."

Enter ps -edf|grep mysql should return around 5 lines of data. Look for mysql in the first column (about the 3rd line down). Its job is pointing back to the root job that started it.

Now to change root's password:
mysqladmin -p -u root --password=newpassord will prompt present the "Enter password:" following instructions above as to what you need to enter at this point

So I think I have a solution to the original questions, but I have to add 1 thing.  I did execute apt-get update, followed by sudo apt-get install mysql-server, followed by sudo apt-get autoremove and walked thru the installs for phpmyadmin, apache2, and mysql-client.  They reported everything was running latest versions.  Now I move onto seeing how to phpmyadmin running (it does not work at this moment).

---

### Post by gkestrel on 2007-11-03
Try this in the terminal enter sudo dpkg-reconfigure mysql-server-5.0 this should allow you to set up a root password

---

