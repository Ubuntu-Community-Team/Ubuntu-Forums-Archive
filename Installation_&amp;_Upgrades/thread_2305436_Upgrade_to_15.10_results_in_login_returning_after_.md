---
title: "Upgrade to 15.10 results in login returning after password is entered"
date: 2015-12-06
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2015-12-06
What should have been an easy night has turned into a nightmare.  Upgrading my secretary's PC to 15.10 so she can use same version of evolution I am using (3.18.2).  Secretary's PC has nvidia graphics GT218 Geforce 4800.  First attempt at upgrade (over existing install -- worked like a champ 3X before) resulted in logon screen coming on as expected (but no nVidia banner as on my Dell laptop) with me sec's name.  I enter her password, screen goes black, and the comes back asking for the password.

I have tried some of the usual fixes (e,g, purging video drivers and starting over, trying nouveau drivers, etc.  When I did a sudo apt-get update && sudo apt-get upgrade, mayh new programs were loaded.  Should have been a winner, but same problem exists.  I can use the PC is Guest mode no problem. CLI works fine.

So, what do I need to do to fix this problem.  I has come up many times before and various fixes exist on the internet.

What is going on with the PC and how do I fix it?

Thank you,

John

---

### Post by ubfan1 on 2015-12-06
The problem probably is in the "hidden" dot files which are used for configurations.  Does the guest session work?  It uses a generated home directory, so the config files are newly created.  You can spend time to track down the specific problem, but you can just backup all the files whose names start with "." (use ls -a to see them all), and then delete them, letting them be recreated.   Seems like the config files are set up for Nvidia, but you are running noveau.

---

### Post by cigtoxdoc on 2015-12-06
Thank you for your help.

First part of solution was to get rid of .Xauthority and .ICEauthority.  That got the login to be stable.  Next problems was that root was the owner of /home/username  .  Once I made username the owner using chown -R, all the problems have gone away.

John

---

### Post by cigtoxdoc on 2015-12-06
I added a user and the problem returned.  When I changed the ownership on home/newusername to newusername, the problem went away.  So while removing the dot files will solve the problem part of the time. changing the directory ownership appears to solve it all the time.  

John

---

