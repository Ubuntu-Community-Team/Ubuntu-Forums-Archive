---
title: "I upgraded to Lucid and all hell broke loose"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gauda_78 on 2010-03-28
Hi guys...
Before you guys say: "Lucid is beta...yada yada yada..."...yeah I know. I am the one
who screwed it up..but I swear..the upgrade somehow was in my update manager so I
only feel partly guilty...lol.
Anyhow...the upgrade to lucid worked out pretty fine..but about a week ago I runned
update manager again..and afterwords I wanted to browse my homefolder, but when I clicked on it it said that no applications was registered to handle it or something..and pretty much nothing in the menu-bar worked..so I rebooted...and after the login..nothing happens
now. I can see the background-picture of my desktop..but no menus, no nothing.
I never used any other than Gnome so I tried to log into KDE, but same thing happen there.
I figured I screwed it up pretty good.
I downloaded and burned a daily-build a couple of days ago cause I thought I could upgrade from the CD and then everything would be fine..but there is only install option there...
Basicly I dont know where to start to debug or what to do..I am a newbie newbie..
Please help! :)
Isnt it possible to upgrade/update and fix all of this from the CD?
I cant wait 1 month to the final release of Lucid, and I dont want to install Koala, cause it was a lot of trouble to get my WLAN, soundcard, and other stuff working...so this time I am facing other fixing my Ubuntu or leaving Ubuntu to Opensuse or something....

---

### Post by bodhi.zazen on 2010-03-28
Hard to know what yoru problem may be from your post, could be a corupted file in your home directory.

I suggest you make a new test user, and if the test user works, move your /home/user to /home/user.bak and make a new /home/user

you can then move your data from /home/user.bak to your new home and delete the /home/user.bak in a week or so.

If that fails, you may need to reinstall, but that seems less likely.

---

### Post by m4tic on 2010-03-28
copy back /home/user/.f-spot

---

### Post by nanog on 2010-03-28
Not enough information in your post. The user switch described by bodhi zazen will fix a  user configuration/permission problem but your problem could be due to a problematic package upgrade. Before going to the trouble of switching users I'd type "Alt-F2" and update your packages in update-manager or synaptic. Post any errors that come up. 

You could also try to see why nautilus and the panel are not working:

Type Alt-F2 and enter "gnome-terminal". 

Post error output after running "killall gnome-panel; gnome-panel" and "nautilus ~".

---

### Post by gauda_78 on 2010-03-29
Thanks for all the good advice! I will try them for sure... :)
But about upgrading/updating...I tried alt-ctrl-F1 and then ping..but I didnt have internet 
connection...
Is it possible to update/upgrade in offline mode somehow???
Oh...and this is probably a really newbie-quez..but howdo I create another user?

(I am running dual-boot with winXP so this is a real pain in the butt)
Thanks a bunch! :)

---

### Post by sdowney717 on 2010-03-29
[http://www.cyberciti.biz/faq/howto-linux-add-user-use-adduser-command/](http://www.cyberciti.biz/faq/howto-linux-add-user-use-adduser-command/)

try this. I have not specifically tried it. But it makes sense.
There are a lot of config files specific to the user account that when they are messed up, stuff happens.

this does work
> scott@scott-desktop:~$ sudo adduser tom
[sudo] password for scott: 
Adding user `tom' ...
Adding new group `tom' (1003) ...
Adding new user `tom' (1004) with group `tom' ...
Creating home directory `/home/tom' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for tom
Enter the new value, or press ENTER for the default
	Full Name []: tom
	Room Number []: tom
	Work Phone []: tom
	Home Phone []: tom
	Other []: tom
Is the information correct? [Y/n] y
scott@scott-desktop:~$ 





> Task: Add a user to the system

Syntax is as follows for useradd command:
useradd <username>

By default user account is locked, you need to setup a new password:
passwd <username>

For example add a new user called tom and set password to jerry:
# sudo adduser tom
# sudo passwd tom

---

### Post by AClark on 2010-03-29
Sounds exactly like what happened to a bunch of us shortly after the release of beta1 - take a look at this thread and see if it doesn't match your situation.

[http://ubuntuforums.org/showthread.php?t=1434160](http://ubuntuforums.org/showthread.php?t=1434160)

Subsequent updates fixed the problem so if you get your panels back as described in that thread you should be able to run update manager and get the fixes.

---

### Post by gauda_78 on 2010-03-29
Tried Alt + F2..nothing happens then...
tried Ctrl + alt + F1 and then adduser tom thing.
Logged into tom, but exactly same problem...:(
Any advice?

---

### Post by sdowney717 on 2010-03-29
did you try
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by gauda_78 on 2010-03-29
yeah, I tried apt-get update thing..but I had no internet...
Anyway..I got it to work by pressing Alt + ctrl + t
then killall gnome-panel; gnome-panel got everything back..menus and everything..
then I did a update and it told me that I had broken package with empathy..so I remvoed empathy and run update..rebooted and everything is good now! :D
thanks specially nanog and all the rest of ya guys! :)
:)

---

