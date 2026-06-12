---
title: "MYSQL Workbench 14.10"
date: 2014-10-24
forum: Installation &amp; Upgrades
---

### Post by lynwode on 2014-10-24
Howdy Folks,
After what appeared to be a seamless upgrade to 14.10 this morning I have hit a snag with MySQL Workbench (6.2.3.12312 64bit) - its broken!

I can no longer connect to remote DBs via SSH (still works via Win7 Vm) and the results grid shows no data for any query even a select count(*) (agian all good in Win 7).
This would suggest its an incompatability issue between workbench and 14.10.

I tried a re-install of Workbench but still the same.

Are there any known issues/workarounds I am blind to?

Cheers,
Tim.

---

### Post by Radams_Roriz on 2014-10-24
i have the same problem, and now?

---

### Post by lynwode on 2014-10-26
Any ideas anyone?

---

### Post by roberto34 on 2014-10-26
Hi, 

I have the same proble, any suggestion?

---

### Post by Scott Deagan on 2014-10-29
I've commented on this bug here: [https://bugs.launchpad.net/ubuntu/+source/mysql-workbench/+bug/1385147](https://bugs.launchpad.net/ubuntu/+source/mysql-workbench/+bug/1385147)

It looks like the Debian guys have already applied a fix for Debian, so it shouldn't be too long before Ubuntu 14.10 is patched.

In the meantime, a workaround is to open up a terminal, create a tunnel using SSH, and then ceate a "Standard (TCP/IP)" connection in MySQL Workbench.

Here are the instructions I provided in the link above:

1. Open up a terminal.
2. Enter: ssh -L 3307:localhost:3306 <email address hidden>
3. Open MySQL Workbench.
4. Create a new "Standard (TCP/IP)" connection.
5. For the hostname, leave the default: 127.0.0.1
6. For the port: 3307 (assuming you've used 3307 as in step 2 above).
7. Enter the rest of your MySQL credentials.

You could also create a ~/.ssh/config entry, as suggested in Andy Turfer's reply:

Host mysql.tunnel
  HostName some-ssh-server.com
  User ssh_username
  IdentityFile ~/.ssh/config/id_rsa
  LocalForward 3307 127.0.0.1:3306


 (of course you wouldn't need the IdentityFile line if you don't have any public/private keys configured)

 
Then you could do the following to establish the tunnel:

 
ssh mysql.tunnel

---

### Post by lynwode on 2014-10-29
Yikes!
I'll wait till its fixed.... thankfully my cough cough win7 vm works.

Thanks for your response though Scott it is appreciated !

Cheers,
Tim.

---

### Post by eriktorsner on 2014-11-13
The problem is with the package python-paramiko. It's upgraded to version 1.15 in Ubuntu 14.10 and that doesn't work well with a lot of SSH servers. I'm not 100% sure why but I've seen mentions of a protocol negotiation issue.

The solution for me was to simply downgrade python-paramiko to the version from Ubuntu 14.04. I did a quick writeup about it here: [http://erik.torgesta.com/2014/11/mysql-workbench-on-ubuntu-14-10/](http://erik.torgesta.com/2014/11/mysql-workbench-on-ubuntu-14-10/)

Quite simply. Download python-paramiko_1.10.1-1git1build1_all.deb and install it using dpkg.

---

### Post by lynwode on 2014-12-04
Thanks for the update but it didn't work for me :(

---

### Post by Sageth on 2014-12-13
If it helps, I've attached the /usr/lib/mysql-workbench/modules/wb_admin_ssh.py where I manually patched it and it's working for me.  Should just be a copy and replace.  

Also, FYI that I'm using mysql-workbench 6.1 from the repos. I don't know if this will work with mysql-workbench-community from the MySQL repo.

---

### Post by phil52 on 2014-12-18
did not work for me.

---

### Post by karthik20 on 2014-12-19
Stop MySQL
The first thing to do is stop MySQL. If you are using Ubuntu or Debian the command is as follows:
sudo /etc/init.d/mysql stop
Next we need to start MySQL in safe mode - that is to say, we will start MySQL but skip the user privileges table. Again, note that you will need to have sudo access for these commands so you don't need to worry about any user being able to reset the MySQL root password:
sudo mysqld_safe --skip-grant-tables &
Note: The ampersand (&) at the end of the command is required.
Login
All we need to do now is to log into MySQL and set the password.
mysql -u root
Note: No password is required at this stage as when we started MySQL we skipped the user privileges table.
Next, instruct MySQL which database to use:
use mysql;
Reset Password
Enter the new password for the root user as follows:
update user set password=PASSWORD("mynewpassword") where User='root';
and finally, flush the privileges:
flush privileges;
Restart
Now the password has been reset, we need to restart MySQL by logging out:
quit
and simply stopping and starting MySQL.
On Ubuntu and Debian:
sudo /etc/init.d/mysql stop
...
sudo /etc/init.d/mysql start
Login
Test the new password by logging in:
mysql -u root -p
You will be prompted for your new password.
 

We followed the above processor to create a New User in Mysql server -5.6 but it is throwing the following error **"already running --Skip grant tables, cannot create user 'admin**".

Please help me out on the above mentioned error.


Regards,
Karthik

---

