---
title: "Update Manager GUI is requesting ROOT password."
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by Martyn Thompson on 2012-10-21
Dear all,

I have been noticing some problems in the last week whereby when trying to perform updates via the graphical Update Manager it has been asking for the root password (not user password as expected with the Ubuntu security model).  

The problem is, I have never set up the root account so although I am aware of its existence, it has never been made active.  

I am able to perform the updates using the terminal however I am concerned that something has happened to my system that could have altered the security settings.  

Does anyone have experience of this?  I am using 12.04 currently and am searching for a fix before I consider upgrading to 12.10.

Thanks.

EDIT: I have noticed this occurs with ANY graphical interface requiring sudo access.  It also happens with "gparted" too.

---

### Post by snowpine on 2012-10-21
Make sure that you launch these applications with **gksu** (or **gksudo**), for example:

```
gksu gparted
```

gksu should ask for your user password (not the root password). Ubuntu is designed to never require root password. :)

---

### Post by 2F4U on 2012-10-21
So what happens if you enter the password of your administrative user?

---

### Post by Martyn Thompson on 2012-10-21
Snowpine

I am able to perform any tasks using the Terminal and as you suggested, using gksudo etc.  

This in itself isn't a problem.  The problem I have is that the system is requesting root access password at all. 

2F4U

For example if I use Dash and type gparted it will bring up the standard dialogue box asking for **root** password.  If I type my own password all that happens is the box wobbles and asks me to re-type root password. 

On my other halfs computer (also running Ubuntu although an older version) the dialogue clearly says "Enter your own password to run administrative tasks".

I am the only user on my machine and have never set up root because it goes against Ubuntu's recommendations (and I have never had to). 

Thanks both for your suggestions.  

In summary - I am able to perform tasks with elevated privileges through Terminal.  However there is still something wrong with the security as if I try and run a task through the GUI directly is requesting a root password.

---

### Post by 2F4U on 2012-10-21
So, just to be clear about that, you did not setup another user (different from the one you created during installation) and are now working under that second user?
Is it possible that the root user has been accidentally enabled by typing

```
sudo passwd
```

This would create a password for root and automatically enable the root accound.

You could try to deactivate the root user by entering

```
sudo passwd -dl root
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by snowpine on 2012-10-21
^--- I agree with the suggestion above.

---

### Post by Martyn Thompson on 2012-10-21
Cheers for both above suggestions gentlemen.

I have only one account on the laptop which I set up.  I haven't run the sudo passwd command however in any case while I was sleuthing around I did discover the other command to disable that (root) account and ran that.  

```
sudo passwd -dl root
```

It has made no difference.  Even logged out/in again and did cold reboot - no changes. 

Yes, I can confirm I set up Ubuntu with only one account many years ago and have performed distribution upgrades ever since (with no serious issues).  

Checked the home folder and there is only my own folder (named martyn) and a mythbuntu user which I toyed with months and months ago - with no success(!).

---

### Post by Cheesemill on 2012-10-21
Open a terminal and run the following command:
```
gksudo gksu-properties
```
Check that Authentication mode is set to sudo (not su).

---

### Post by Martyn Thompson on 2012-10-21
Thanks for this cheesemill.  

I checked that and it was set correctly (sudo).  I have never seen that little command before. 

I got a screen-dump of to show the example of what is happening.  This is when I tried to run gparted from the Dash but it happens with anything required elevated privileges. Note that it requests root password and not account or user password. 

[IMG]http://www.ansuk.org/root.gif[/IMG]

---

### Post by Cheesemill on 2012-10-21
I'm just guessing but you could try:
```
sudo dpkg-reconfigure gksu
```

If that doesn't work try the command again with sudo instead of gksu, it can't hurt (as you can see I really am clutching at straws here) :)

---

### Post by sisco311 on 2012-10-21
Please post the groups you are a member of:
```
id
```

And the content of polikt and sudo config files:
```
sudo cat /etc/sudoers
cat /etc/polkit-1/localauthority.conf.d/*
```

---

### Post by Martyn Thompson on 2012-11-05
Sorry for delay in replying... I have been doing all by command line then realised this was still an issue...

Here are outputs requested. 
```
uid=1000(bob) gid=1000(bob) groups=1000(bob),4(adm),33(www-data)

```

```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
bob ALL=(ALL) ALL

```

```
martyn@Aspire-5551:~$ cat /etc/polkit-1/localauthority.conf.d/*
# Configuration file for the PolicyKit Local Authority.
#
# DO NOT EDIT THIS FILE, it will be overwritten on update.
#
# See the pklocalauthority(8) man page for more information
# about configuring the Local Authority.
#

[Configuration]
AdminIdentities=unix-user:0
[Configuration]
AdminIdentities=unix-group:sudo;unix-group:admin

```

Noticed that the final output mentions unix-group:admin whereas my id states I am in the group **adm** but not **admin**.  Is this relevant?

---

### Post by sisco311 on 2012-11-05
> **Martyn Thompson said:**
> Sorry for delay in replying... I have been doing all by command line then realised this was still an issue...

Here are outputs requested. 
```
uid=1000(bob) gid=1000(bob) groups=1000(bob),4(adm),33(www-data)

```

```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
bob ALL=(ALL) ALL

```

```
martyn@Aspire-5551:~$ cat /etc/polkit-1/localauthority.conf.d/*
# Configuration file for the PolicyKit Local Authority.
#
# DO NOT EDIT THIS FILE, it will be overwritten on update.
#
# See the pklocalauthority(8) man page for more information
# about configuring the Local Authority.
#

[Configuration]
AdminIdentities=unix-user:0
[Configuration]
AdminIdentities=unix-group:sudo;unix-group:admin

```

Noticed that the final output mentions unix-group:admin whereas my id states I am in the group **adm** but not **admin**.  Is this relevant?

Yep. It seams that you somehow removed your user from the admin and sudo groups, then manually edited the sudoers file in order to regain full sudo rights. But  to use polkit to authenticate yourself as an admin with your user's password you need to be a member of the admin or sudo group:
```
sudo gpasswd -a bob admin
```
or
```
sudo gpasswd -a bob sudo
```

---

### Post by Martyn Thompson on 2012-11-05
```
sudo gpasswd -a bob sudo
```

That second command worked perfectly thank you. The first command (admin) replied with an error saying:

```
gpasswd: group 'admin' does not exist in /etc/group
```

Thanks for the support- I will add a 'solved' to the heading. 

Best wishes all.

---

