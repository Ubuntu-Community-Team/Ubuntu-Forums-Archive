---
title: "How to restore Ubuntu 9.10 to all the defualt configurations ??"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by thyag on 2010-02-15
Hi,

I just got installed ubuntu karmic koala 9.10 on my laptop and fiddle too much with the system configuration files. Now I notice that most of my permissions are not working in my login. How do I restore my Ubuntu setting, which are as good as freshly installed OS and also Not disturb any of my currently installed application on the system ??

Note: I repeat "I really dont want to disturb my of my currently installed applications on my ubuntu and yet want to restore my system to freshly installed OS settings. All the applications that I have installed is a whopping 3 days of googling and hardwork in getting them working :-( "

Some of the freaky things happening in my system:

1. I am not able to see Battery notification and Network notification
      My workaround: execute "sudo /usr/bin/gnome-power-management" and "sudo /usr/bin/nm-applet"

2. I am not able to lock my screen
3. I am not able to access my windows drive. Which otherwise when worked normally used to prompt me to enter my password, post authentication I was able to access my drive.
4. I am not able to change time zone.

Pl help me here !!

-Thyag

---

### Post by Cheezespread on 2010-02-15
> **thyag said:**
> Hi,


Some of the freaky things happening in my system:

1. I am not able to see Battery notification and Network notification
      My workaround: execute "sudo /usr/bin/gnome-power-management" and "sudo /usr/bin/nm-applet"

2. I am not able to lock my screen
3. I am not able to access my windows drive. Which otherwise when worked normally used to prompt me to enter my password, post authentication I was able to access my drive.
4. I am not able to change time zone.
Pl help me here !!
-Thyag


1. You mean on the panel , rt ?. Right click on the panel and add to the panel. You would be able to see the options in there. I beleive Notification area is the one .

3. ```
sudo fdisk -l
``` . Can you see if Linux is identifying your windows partitions?

---

### Post by thyag on 2010-02-15
Hi,

> I have tried added Notification in the panel, that didn't suffice my need :(
> Yes the windows file system is visible !!

---

### Post by pmlxuser on 2010-02-15
try removing all the gnome configuration files

```

sudo rm -rf .gnome* .gconf*

```
log out log in

---

### Post by Cheezespread on 2010-02-15
> **thyag said:**
> Hi,

> I have tried added Notification in the panel, that didn't suffice my need :(
> Yes the windows file system is visible !!

Could you elaborate on that ? You mentioned you needed the network applet.

Could you post the output of the command please ?

---

### Post by thyag on 2010-02-15
Hi,

Firstly removing the gnome conf files logout and login didnt work for me.

Ok here is what I did to get the notification of the network and the battery/power
Right click on the panel --> Add to panel  -- > Selected notification area
This doesn't get the Battery/power charging icon on the panel and also doesnt get the network links (wireless/wired)

Also I am not able to access any windows partitions. It says "unable to mount file system" Authentication required. But the authentication windows where I can enter my password doesn't show up at all. "Have attached a snapshot too fyi pl"

Pl let me know if you need more info !!

-Thyag

---

