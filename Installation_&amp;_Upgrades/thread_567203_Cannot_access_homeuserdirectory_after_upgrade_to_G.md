---
title: "Cannot access /home/user/directory after upgrade to Gutsy Gibbon beta 1"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by guris on 2007-10-04
Hi. I have this problem after upgrading to gutsy beta. When I access my /home/user/ folder nautulus crashes. I can browse this files with  sudo nautils and cd terminal but I cannot watch my movies play mp3 or play any games that are in thisi directory. All my files and programs are in this dir and I cannot access them as a user after  upgrade. I cannot figure miself why nautilus hangs. This is error msg: 

"Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem." 

I tried killing bono and nautilus and it still doesn't. Could someone  exlpain what this error message means?  and  can I see system log to diagnose this problem?  
Thank you any advise will be appreciated.

---

### Post by d_in_Conduct on 2007-10-04
This used to happen to me when I upgraded early Mandrake distros.  Try this:
sudo nautilus and go to the /home directory.
Right-click your user directory and click Properties.
Click the Permissions tab and make sure you are still the owner.  If you have to change it, be sure to check the box that makes the changes to everything inside the directory.

Hope this helps.

---

### Post by guris on 2007-10-05
No the permissions are OK. I actually can access this directory but it opens really slow. I have some files there that I use as icons with kiba dock and my movies and mp3s. I will try to move that files to another directory and see if that help. but I don't think that's the reason :(. It never happend before :confused:
Thanks for reply.

---

### Post by dabl on 2007-10-05
You haven't inadvertently almost filled up a partition, have you?  That will cause things to slow down or stop.  :)

---

### Post by guris on 2007-10-06
I upgraded to gutsy today and everything works fine now :) exept wifi :(( I must wait until full version comes out or get back to fiesty :(.  Hope wifi will work in new verion :).

---

### Post by forestpixie on 2007-10-06
you wifi problem is I expect due to the restricted-kernel module being held back - there are threads here and in Gutsy forum about the same, it'll turn up when they're ready :)

I'm in same boat but using the old kernel I can do what I need to

---

### Post by guris on 2007-10-06
Sorry double post. 
thanks for help guys.
I have downloaded and installed firmware through restricted drivers manager, I can see network but cannot connect. It says no network after few minutes. :( 
hope it will be fixed in next update

---

