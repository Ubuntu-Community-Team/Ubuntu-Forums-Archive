---
title: "FYI - Update Manager Not Updating"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by DoctorTux on 2007-08-08
Hello all.  One of the most common problems new users of Ubuntu are facing is that the Update Manager doesn't update after notification of new security fixes and other stuff.  I just installed Ubuntu 7.04 desktop on my machine after having worked with SuSE Linux since version 9.0.  (Oops!  Did I just cuss and say the four letter "S" word? :oops:  )  Anyway, I had problems with Update Manager too in Ubuntu.  It just seemed to hang and hang and wouldn't update and install even one file.  At first I thought it was a firewall problem.  But having worked with S*** Linux, it had a utility called YaST which I always had to log in as "root" to update the system.  That got me thinking.  When I installed Ubuntu, it asked "Who are you?"  I didn't say I was "root".  The user Ubuntu created me under allows me to do many administrative tasks, but system updates is obviously not one of them.  It seems to have defaulted me to more of a superuser than root.  When I went into System > Administration > Login Window, I clicked on the Security tab and checked the checkbox "Allow local system administrator login".  That allowed me to log into Ubuntu as "root".  With full root privileges, Update Manager works as pretty in Ubuntu as it does in S*** YaST.  I have not tested this yet by changing my own username's Main Group to Admin.  I'm assuming I already have that privilege.  I sure don't want to keep my username as a "root" privilege.  That' s a security threat to the 10th power!  If we must be logged into Ubuntu with "root" privileges to use Update Manager, it needs to be documented in Ubuntu's online help system.  Does any good penguin out there know how to reach the technical writer for Ubuntu's online help documentation?  Maybe Ubuntu developers will find a way to tunnel through Update Manager with root privileges without logging into the whole dang operating system as "root".  If you do that in S***, the wallpaper turns bloody red and shows lit fuses on bombs.

---

### Post by aysiu on 2007-08-08
You don't need to enable the root login in order to do anything in Ubuntu.

Read more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

By the way, my update manager works just fine.

---

### Post by eentonig on 2007-08-08
You do know that you have to click the notification to activate the actual installation of updates, do you? First you'll see what is about to being updated. And then you click on 'install'. This will ask you for yout 'sudo-pasword'.

---

### Post by DoctorTux on 2007-08-08
Thanks aysiu.  I knew there had to be a way.  I'll start doing it your way from now on and mine should work just fine too.

---

