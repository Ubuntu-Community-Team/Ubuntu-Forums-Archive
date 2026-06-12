---
title: "Re-installation gone wrong 12.04"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2012-09-17
I decided that it would be best to reinstall. I choose to format the / partition and point in the installation to /home which is on a seperate partition. Despite setting up a name and password, which was the same as the previous installation, I can not log in as administrator.  My password is not being recognised. I have done the reinstall again and I have the same problem. I guess it is connected with the dvorak keyboard layout. I wonder if querty is being applied befor login and dvorak after. This should not happen and has not in the past but I do not know any other reason for correct password to be rejected. 

I think the wrong home location is being used and I do not know how to change it or check it from within the guest user. 


Display shows that I am working on a single screen laptop instead of a double screen desktop.


I have never had this trouble before. I have often reinstalled the os and had no problem loggiing in. Now I can not do it other than as guest.


What should I do? 

What CLI would you like me to run?


Robin

---

### Post by Robbyx on 2012-09-17
I thought I would check fstab but first needed to confir the id of the partitions:

guest-of2qMV@robins-EP35-DS3L:~$ sudo blkid
sudo: unable to change to sudoers gid: Operation not permitted
sudo: setresuid() [0, 0, 0] -> [116, -1, -1]: Operation not permitted
guest-of2qMV@robins-EP35-DS3L:~$

---

### Post by doktorOblivion on 2012-09-17
I you tried yet to go into Recovery Mode during boot to see if sudo is recognized then?  If it is, you could perhaps figure out if your sodoers file is corrupted or something like that...if you can read it what does it say?  Can you append it here?

---

### Post by Robbyx on 2012-09-17
> **doktorOblivion said:**
> I you tried yet to go into Recovery Mode during boot to see if sudo is recognized then?  If it is, you could perhaps figure out if your sodoers file is corrupted or something like that...if you can read it what does it say?  Can you append it here?

I have made some good progress in getting around but not solving this, because I do not understanding why it happened.

I was able to create a new admin (robins1) user and set up the dual screen. 

I created a new user (robins1) without the old one's (robins) home content. What is the best way to copy the old user's home content to the new user? 

Alternatively, if I renamed the old robins home directory to robins1  and the new one robins1 to robinnew and logged in as robin1 do you think I will be able to login without any problems and have access to all of robins' home  content? It all depends if anything was in the old user's home that was blocking the login process. Do you know if this will work and where the cause of the block in logging on would be stored?




Robin

---

### Post by Robbyx on 2012-09-17
This is the current Sudoers. I doubt if it changes by my creating a new user:

#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

---

