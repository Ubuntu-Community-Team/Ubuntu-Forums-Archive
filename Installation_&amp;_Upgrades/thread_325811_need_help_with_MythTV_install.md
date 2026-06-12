---
title: "need help with MythTV install"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by mageus on 2006-12-26
Would like some help with a mythtv install.

I've spent the last 3 days trying to setup mythtv and seem to have it somewhat working now, but still getting many errors.

Setup:
	Ubuntu 6.10 Edgy
	Nvidia 7600GT
	Hauppauge PVR-150
	frontend/backend installed on same machine

I set up mysql and the ivtv driver, and confirmed that a video feed out of /dev/video0, the installed Myth.
After many problems with logging into mysql, setting up the backend, many purge and reinstalls of the above software, I am now able to view TV sporadically through the frontend, but have some issues:


- The mythbackend log shows the following:

No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.

Mysql is running and I can log into it via phpmyadmin.  The backend log shows it's connecting to the mythconverg db.  When I run mythtv-setup, it shows 127.0.0.1 as the local and master server addresses.  my.cnf shows the IP address correctly in the 'bind address' section.  So why does the backend not see the address?

- There is no mysql.txt file in my ~/.mythtv directory.

There is, however, a mysql.txt file in my usual user's home directory.  I did the install of mysql and mythtv using synaptic under my usual user login, but I ran mythtv-setup from the mythtv account.

- When starting mythfrontend the terminal displays:

mythtv: could not connect to socket
mythtv: No such file or directory

However, it's able to connect to the database and launch OK (sometimes).



I'm able to watch TV sporadically, but at other times myth-frontend gives the message

could not connect to the master backend server


Any help on why my installation is set up in such a strange way would be appreciated.  I can post logs if needed.

---

### Post by xboxer21 on 2006-12-26
try this 
sudo nano /etc/mysql/my.cnf
comment out that line bind-address= 127.0.0.1
sudo /etc/init.d/mysql restart

Then restart mythtv backend and try connecting to it using the frontend.

Thanks

---

