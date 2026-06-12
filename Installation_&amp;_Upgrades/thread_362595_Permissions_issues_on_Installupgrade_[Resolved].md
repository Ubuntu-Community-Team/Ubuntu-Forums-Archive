---
title: "Permissions issues on Install/upgrade [Resolved]"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by Romanmir on 2007-02-15
I am having a problem with permissions. I am trying to install Edgy on a 160gb HDD partitioned all to heck. 

I can boot to GDM. 

I cannot login. It tells that it cannot create any files in my home folder as the Permissions are denied.
I have been able to login to the failsafe command line terminal.
I can view the files themselves using the root user (sudo -s)
I have looked at the current passwd file, and the uid and gid are both 1000.
I have verified that all files in the home directory are user:1000 group:1000

I have tried to chown -R user:group on the folder in question.

Aside from now using UUIDs, the fstab file looks ok. I have verified that the uuid for the home partition is correct.

no luck.. 
](*,) 

I am fairly comfortable in the command line but I'm stumped as fas how to get access to my files or even log in as my user in a normal fashion..

any ideas? questions?

---

### Post by aysiu on 2007-02-15
You say you're *trying* to install Edgy?

Or you already *have* installed Edgy?

In either case, you probably don't have a lot of special customizations in your home directory, so I would suggest creating a new user and logging in as that user--you can always copy over later your personal files (music, documents, pictures, etc.) to this new account.

Let's say, for the sake of these examples, your new user will be called *roman*. You can call the new user whatever you want, though--as long as it's not the same name as your old user (the one you're having trouble logging in as).

Boot into recovery mode (this will make you root), then type: ```
adduser roman
adduser roman admin
reboot
``` Then boot into normal mode and normal Gnome (not failsafe), logging in with *roman*. If that works, press Alt-F2 and type ```
gksudo nautilus
``` You can then copy over any personal files you need from your old user's folder to your new user's folder. Don't copy configuration files, just personal files.

Eventually, you'll want to add this new user to other groups besides *admin* (like *audio*, for example). I believe if you go to System > Administration > Users & Groups, you can do this graphically.

---

### Post by Romanmir on 2007-02-16
Sorry, I was successful in installing edgy.

I was not succeful in logging in seamlessly..

Anyway, I tried your advice and it seems to be working.

Thanks for your help.

---

### Post by aysiu on 2007-02-16
I honestly don't know what happened, but I'm glad it's working now.

The only way I know to accidentally change permissions on your home directory is launching a graphical application with *sudo* instead of *gksudo*. Read more here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

