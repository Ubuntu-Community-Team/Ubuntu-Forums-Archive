---
title: "root password?"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by pullmoll on 2009-11-23
After once using the *Users and Groups* dialogue to add another user, now the system began to ask for the password of **root**, e.g. when trying to install another application using the software center.

It doesn't accept my password, but want's that of root, who has no password set.

Anyone else experienced this oddity?

---

### Post by snowpine on 2009-11-23
Hi Pullmoll, there is no "root password" in Ubuntu; it is locked for security purposes.

The first user you created at installation will have admin priviledges and can use "sudo" to temporarily gain root priviledges. Users you create yourself will not have this ability unless you add them to the "admin" group.

If something's messed up, here's a good guide to troubleshoot: [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by reeboker on 2009-11-23
> **pullmoll said:**
> After once using the *Users and Groups* dialogue to add another user, now the system began to ask for the password of **root**, e.g. when trying to install another application using the software center.

It doesn't accept my password, but want's that of root, who has no password set.

Anyone else experienced this oddity?


This could be help. [https://help.ubuntu.com/community/RootSudo#Enabling the root account]("https://help.ubuntu.com/community/RootSudo#Enabling the root account")

---

### Post by pullmoll on 2009-11-23
> **snowpine said:**
> Hi Pullmoll, there is no "root password" in Ubuntu; it is locked for security purposes.

I knew that (and wrote it in my question) there is no such thing as a "root password". But take a look at this screenhot:
[[IMG]http://img2.imagetitan.com/img2/small/31/31_auth.png[/IMG]]("http://img2.imagetitan.com/img.php?image=31_auth.png")

It is not sudo that's broken, but the GUI dialogue asking for authentication. I do not want to install a root password, but I want the authentication to ask me for my password again, as it did before...

---

### Post by pullmoll on 2009-11-23
> **reeboker said:**
> This could be help. [https://help.ubuntu.com/community/RootSudo#Enabling the root account]("https://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account")

Nope. I don't want to enable the root account, I rather want the system to ask me for my password again :-D

---

### Post by aysiu on 2009-11-23
**Step 1**
Check your /etc/sudoers file to make sure it looks like this: ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
[color=red]**%admin ALL=(ALL) ALL**[/color]
``` The proper way to edit that file is with the command ```
sudo visudo
``` It checks for syntax errors before you try to save the file.

**Step 2**
Check the /etc/group file to make sure your username belongs to the group *admin*. There should be a line in there that looks something like ```
[color=red]**admin**[/color]:x:115:[color=red]**pullmoll**[/color]
```

**Step 3**
Check your /etc/shadow file. There should be a line that looks something like this: ```
[color=red]**root:!**[/color]:14522:0:99999:7:::
``` The really important part is that there should be an exclamation point after the *root:* and not an actual hashed password.

---

### Post by lisati on 2009-11-23
Have a look here for some of the background on the Ubuntu way of doing things in this situation: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by pullmoll on 2009-11-23
> **aysiu said:**
> **Step 1**
Check. Exactly as you listed it.

> **Step 2**There you go! My login name (pm) was no longer listed in the admin group.

>  **Step 3**
Check your /etc/shadow file. There should be a line that looks something like this: ```
[COLOR=red]**root:!**[/COLOR]:14522:0:99999:7:::
``` The really important part is that there should be an exclamation point after the *root:* and not an actual hashed password.I have ```
root:!:14562:0:99999:7:::
``` there. Is the number some kind of umask?

BTW: The vanishing of my login name in the /etc/group happened without me touching the file. All I did was using the GUI group/user manager. I'll try again if I can reproduce the effect.

Thanks for your help!
pullmoll

---

### Post by sisco311 on 2009-11-23
> **pullmoll said:**
> 
I have ```
root:!:14562:0:99999:7:::
``` there. Is the number some kind of umask?


[http://www.cyberciti.biz/faq/understanding-etcshadow-file/]("http://www.cyberciti.biz/faq/understanding-etcshadow-file/")
  

> **pullmoll said:**
> 
BTW: The vanishing of my login name in the /etc/group happened without me touching the file. All I did was using the GUI group/user manager. I'll try again if I can reproduce the effect.

Thanks for your help!
pullmoll

You probably unchecked the Administer the system box and users-admin (Users and Groups) removed your user from the admin line of the /etc/group file.

In order that the new group membership take effect you have to start a new login session (log out and log back in the user in question).

i.e. if you add your user to a new group, the 
```
id
```
command will not list the new group until you log out and log back in.

So, if you remove your user from the admin group, you can still use sudo until you start a new login session.

It looks like that policykit (the GUI authentication window) determines the users group membership by reading directly the /etc/group file. That's why once your user is removed from the admin group you can not use policykit to authenticate yourself as an admin.

---

### Post by aysiu on 2009-11-23
Cheap plug for this Brainstorm idea:
[Idea #11107: Users and Groups should always make sure at least one user is in the admin group](http://brainstorm.ubuntu.com/idea/11107/)

---

### Post by pullmoll on 2009-11-24
Ok, it looks like there's more brokenness in the passwd file. Here's what's now left in my passwd file: ```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
syslog:x:101:102::/home/syslog:/bin/false
messagebus:x:102:106::/var/run/dbus:/bin/false
avahi:x:105:111:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
haldaemon:x:107:114:Hardware abstraction layer,,,:/var/run/hald:/bin/false
gdm:x:112:119:Gnome Display Manager:/var/lib/gdm:/bin/false
pm:x:1000:100:pullmoll,,,:/home/pm:/bin/bash
tinyproxy:124:124::/nonexistent:/bin/false
```I'm sure there's a whole lot of (pseudo) users missing here, and I didn't remove them intentionally.
The only thing I did after install was ```
sudo vipw
``` to change the group of my account to 100 (users) instead of the personal group 1000 (pm), which was created by setup.
Later I used the GUI group + user management to add another user (sasa). I wondered that no users were listed in the selection box, but thought that perhaps there was a filter for pseudo and primary users in action. Then when the GUI tool suggested to use UID 1000 for the newly created account, that seemed a little odd to me. I changed it to use UID 1009 instead and set the group to 100 in the settings, then saved the changes. I guess this is where I lost most of my /etc/passwd and /etc/shadow file contents. I only don't know why.

I'll later try to install ubuntu-9.10 in a virtualbox to see which accounts were lost. I guess there's no backup of the files hidden in /var somewhere!?

---

### Post by sisco311 on 2009-11-24
> **pullmoll said:**
> I guess there's no backup of the files hidden in /var somewhere!?

/etc/passwd-
/etc/shadow-
/etc/group-
/etc/gsadow-

and

/var/backups/passwd.bak
/var/backups/shadow.bak
/var/backups/group.bak
/var/backups/gshadow.bak

---

### Post by pullmoll on 2009-11-24
> **sisco311 said:**
> /etc/passwd-
/etc/shadow-
/etc/group-
/etc/gsadow-

and

/var/backups/passwd.bak
/var/backups/shadow.bak
/var/backups/group.bak
/var/backups/gshadow.bak

*sigh* It's too late. The backups are the same as the current status :-/ I've got to find the missing entries elsewhere.

---

