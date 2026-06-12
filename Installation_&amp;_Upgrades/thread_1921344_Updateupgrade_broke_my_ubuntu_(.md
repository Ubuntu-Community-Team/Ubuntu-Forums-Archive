---
title: "Update/upgrade broke my ubuntu :("
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by bikewrecker on 2012-02-06
Hi all, I'm running ubuntu 11.10 and whenever I bootup ubuntu the first thing I always do is 
$sudo apt-get update 
$sudo apt-get upgrade
today I think this broke my ubuntu :(

After doing this some of the code I was working on was acting funny even though it was acting perfectly fine last time I was running it, so I decided to reboot. Now when I boot to my ubuntu partition I get a loading screen then the login screen. If I try to login the screen goes blank for a bit then it shows me the login screen again. If I type in the wrong password it does nothing but tell me I typed in the wrong password. The buttons in the top right to tell it to reboot/restart don't do anything so I'm forced to crtl-alt-f6 to get to a command line from where I can reboot it. 

No idea whats happening or what I can do to fix it. Is there a way to un-do the upgrade from the command line?

Much appreciated - bikewrecker

---

### Post by bikewrecker on 2012-02-06
bump. I really need my ubuntu partition working for my job...

---

### Post by jayshomebrew on 2012-02-07
reboot computer, hold down <shift> [IMG]http://img441.imageshack.us/img441/9581/tmpvwnpdq.png[/IMG] to show grub menu. 
[IMG]http://www.howtogeek.com/wp-content/uploads/2007/09/image55.png[/IMG]
Select previous kernel and boot up.
If the previous kernel works fine, use synaptic to remove the newer kernel.
[IMG]http://www.cnx-software.com/wp-content/uploads/2011/04/synaptic_remove_old_kernels_ubuntu.png[/IMG]

then do a:
```
sudo update-grub
```


If you don't know how to remove the old kernels, take a look here:
[http://www.cnx-software.com/2011/04/07/removing-old-kernels-in-ubuntu-with-synaptic/]("http://www.cnx-software.com/2011/04/07/removing-old-kernels-in-ubuntu-with-synaptic/")

---

### Post by bikewrecker on 2012-02-07
yea i tried to load the older kernals but they did the same thing :( thanks for the reply though

---

### Post by jayshomebrew on 2012-02-07
maybe this is the same problem you have:
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/871667]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/871667")

if you can get to a term (<ctrl><alt>-f2) go ahead and delete your .Xauthority

if you can't get to a term, go ahead and boot the ubuntu live-cd, mount your drive, then delete your .Xauthority folder.

You can also try adding another user via the command line, and logging on using that user.
[https://help.ubuntu.com/community/AddUsersHowto]("https://help.ubuntu.com/community/AddUsersHowto")

---

### Post by bikewrecker on 2012-02-07
Ok, I made a new user and tried to get in that way, but I got the same result. Screen goes black for about 2 seconds then brings up the login screen again. I tried deleting the .Xauthority file/folder too, but that didn't work either.  Thank you so much for the suggestions though. I think it's lightdm that is giving me issues but idk how to reset it or w/e I need to do.

---

### Post by bikewrecker on 2012-02-07
Ok I got it fixed finally!!!!!!!! I think what was happening was that gdm and lightdm weren't cooperating with eachother. I typed
 
$sudo aptitude remove lightdm 

then I tried to do 

$sudo aptitude install lightdm 

but I got a bunch of errors and it wouldnt install.... Luckily blind and dumb luck kicked in and I can log in now; however, a bunch of stuff doesn't work now including my terminal, my wifi, and my mozilla wont even open, but this is kindof a different issue so I'm going to make a new thread. 

Thank you to all of those who gave your suggestions!

---

