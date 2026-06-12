---
title: "Can't Choose Desktop Manager on Login"
date: 2014-11-18
forum: Installation &amp; Upgrades
---

### Post by DeborahSu on 2014-11-18
I'm getting a bit frustrated. I really really really dislike the Unity desktop and want to use the classic Gnome instead. When I go to log in, I have NO choice of desktop manager at all. Gnome is of course installed, since it's the base for Unity.

Background: I've been using Ubuntu for years now. I updated to 14.04, but it wouldn't load even so far as the login screen. I read somewhere that it is probably because my older motherboard doesn't support some protocol that I can't remember now, so I reinstalled 12.04. It didn't give me the choice for advanced and wound up overwriting everything, so all of my old data is gone. This made me pretty unhappy, of course, but that was my fault. I've installed & updated so many times without issue that I didn't bother backing anything up, and I have a hunch that I was running 32 bit before, and installed 64 bit .... Now, I seem to be stuck with Unity. Help, please?

---

### Post by deadflowr on 2014-11-18
Install gnome-panel.
Try this
When you get to the login screen, press ctrl + alt + F2
enter your username and password.
Then try
First make sure the system is fully up-to-date
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
The install the gnome panel
```
sudo apt-get install gnome-panel
```
Let it in install the packages.
When it finishes install gnome panel, enter
```
sudo service lightdm restart
```
you should now see the login screen and in the username password box if you toggle the little box in the right corner, you should now have entries for gnome (I can't remeber if they will be fallback or flashback, but you should have two new entries, one for effect and one for no effects)

For the record, Ubuntu is gnome based, that does not mean it'll have the gnome interface.
Unity is Ubuntu's interface in place of the standard/normal gnome interface.
As posted, to get the gnome interface, or variants thereof, you need to install it.

Hope this helps.

---

### Post by DeborahSu on 2014-11-18
> **deadflowr said:**
> Install gnome-panel.
Try this
When you get to the login screen, press ctrl + alt + F2
enter your username and password.
Then try
First make sure the system is fully up-to-date
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```


Won't that try to upgrade me to 14.04, which doesn't work on my computer?

---

### Post by deadflowr on 2014-11-18
No, to upgrade versions you run the command do-release-upgrade.
dist-upgrade is completely within the current version.

---

### Post by DeborahSu on 2014-11-18
I tried it ... no update or upgrade available, and neither was gnome-panel. I searched gnome-panel in the software program and it said it couldn't access "universal" source, which is really weird. I seem to recall that I installed the 32-bit to begin with because 64-bit was pretty buggy ... guess I'll try going back to it and see if that works better.

Thanks for your help!

---

### Post by deadflowr on 2014-11-18
Well, my initial propose to log into ctrl+alt+F2 was to avoid unity, but I guess there is no choice.
Try logging in normally, into unity, and rerun the commands in a terminal and copy the output, and paste them here, in this thread.

You might also look to see if somehow universe was disabled.
In a terminal run
```
software-properties-gtk
```
In the page that opens the sceond entry should say community-supported something (universe)
Make sure it has a check in the box.
If no check, then check it(mark it and it'll add a check)
Then close the window, and if it does not ask to reload, then re run the update commands again...

---

### Post by DeborahSu on 2014-11-18
Universe has not been disabled--there is a checkmark next to it. This is my output:[INDENT]
```
deborah@deborah-GA-890GPA-UD3H:~$ software-properties-gtk
gpg: /tmp/tmpr2wb70/trustdb.gpg: trustdb created
deborah@deborah-GA-890GPA-UD3H:~$ sudo apt-get update
[sudo] password for deborah: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates InRelease 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
deborah@deborah-GA-890GPA-UD3H:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
deborah@deborah-GA-890GPA-UD3H:~$ dist-upgrade
dist-upgrade: command not found
deborah@deborah-GA-890GPA-UD3H:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
deborah@deborah-GA-890GPA-UD3H:~$ sudo apt-get install gnome-panel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-panel is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gnome-panel' has no installation candidate
```
[/INDENT]

---

### Post by deadflowr on 2014-11-18
Now everything makes sense.

You are not running 12.04, but 12.10.(quantal)
Ubuntu 12.10 is no longer supported, and as such no packages are available anymore.

Unfortunately, you'll need to reinstall again.
Look here for 12.04
[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

If you need a version of precise/12.04 that used the original kernel versiom(version 3.2) look at this page
[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)
Scroll down the page to see the list of versions
You want the iso file marked
[COLOR=#772953]ubuntu-12.04-desktop-amd64.iso[/COLOR]             25-Apr-2012 16:13  698M  Desktop CD for 64-bit PC (AMD64) computers (standard download)
For 64-bit version
or
ubuntu-12.04-desktop-i386.iso[FONT=Verdana]              23-Apr-2012 12:27  701M  Desktop CD for PC (Intel x86) computers (standard download)
for 32-bit version

This is a fully supported version, and after installation, an update will be needed to bring it up-to-date.

The reason to install the 12.04 version over the 12.04.5 version is because the 12.04 version has ann older hardware stack that should work on your system.
The 12.04.5 version has an updated hardware stack. The 12.04.5 hardstack is based on the hardware stack used in 14.04, so it is possible that that stack might not work well, since you already know that 14.04 does not work well.

Hope this helps[/FONT]

---

### Post by DeborahSu on 2014-11-18
Thank you!!! Hopefully, that'll get me back up & running. I'll let you know!

---

### Post by DeborahSu on 2014-11-30
It took me a little while, since my dvd drive decided to bite the dust. I got a flash drive, got it installed, did the commands as instructed, and I'm back up & running! Thank you SOOOOO much!!!

---

