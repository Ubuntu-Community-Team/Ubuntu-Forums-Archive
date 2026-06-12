---
title: "Something went wrong during install"
date: 2004-11-04
forum: Installation &amp; Upgrades
---

### Post by Northdude on 2004-11-04
I don't know where I messed up, but I sure did! Yesterday I formatted my gentoo system to install win2k and ubuntu in a dual boot setup. 

The ubuntu setup went fine, but for an unknown reason, the user I created during the setup procedure did not exists at the end. Well, I rebooted back in failure mode and tried to create it but adduser complained that this user home directory could not be created. Hmmm, ok. So I created the home directory by hand and then proceded to create the user. The next problem is that while logged in as root (I setted a root pwd while in failure mode), whenever I tried to chown the /home/user directory to this new user, it gave me a "operation not permitted" error. This is kind of frustrating cause I can't log in gnome using root to see if there is any tools to help me and whenever I try to log using this user I created, I get errors because gnome can't create the proper user files... Is there something else then adduser that I should use under ubuntu? And why can't I chown the home directory at all?!? I quite confused... 

Ô yeah, my adsl connection isn't setted up either! Is the pppoe packages already on the cd? I read a lot of good things about this distro so I really want to got it working. Comming from a gentoo background (and suse at my job), I don't mind making things to work with a bit of elbow grease! But I've never tried a debian system before nor did I ever encountered those kind of problems so some help would really be appreciated!

Ciao!

P.S.: I think this emoticon is appropriate hehe  ](*,)

---

### Post by randy on 2004-11-04
Are you running chown as root or using sudo.  You should run it with the -R option.

---

### Post by Northdude on 2004-11-04
I tried the "chown" thing both as root and with sudo while logged in as a user. I just stumbled on this post and this is exactly the same problem I have :

[http://ubuntuforums.org/showthread.php?t=1864&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=1864&page=1&pp=10)

My second hd is formatted using a fat32 partition (both accessible from my win2k and linux system) and I was getting the same problem as this guy; "looping" in the install while creating my user, and the same "chown 1000:1000 /home/user: Operation not permitted" error.

---

### Post by txema on 2005-10-31
same problem, "looping" of the create main user prompts during installation. can only login in recovery mode, using root passwd and then "startx" to get to main screen.

"adduser" ("user does exist/ not exist") will not work, the GUI for creating user/ groups allows me to do so but after reboot in normal mode i can only login to receive a failure message after which i am logged off again.


would be nice to get some help on this one :)

apart from this, i (linux semi-newbie) am quite happy with installation, hardware recognition and overall appearence of ubuntu.

tx.

---

