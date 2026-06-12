---
title: "After new installation can't login as root!"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by daidainius on 2006-11-24
Hi,
I installed Ubuntu to HDD. I was asked only for user name and password. Now I  can't login as root. I have tried all the passwords I can image('admin', 'administrator', my user passw, 'ubuntu', '123456', '1234' and ect....) in upper/lower cases, but unsuccesfully.
Must be some predefined first installation password for user root!
May somone help?

---

### Post by dogon on 2006-11-24
You're right, there is no password, and root login is disabled by design.

You can do what you wish to do with sudo.

If you wish to execute a command as root type "sudo <command>"

if you want a root shell, type "sudo -i"

I suggest you try it with this, it should suffice.

If you want root back, I'd say open a rootshell and just change the root password. It should work because the root home environment is still intact. I have not tried this myself because I think the sudo root access is really all that I need. And I thought the hidden root user was kinda clever.

---

### Post by timcredible on 2006-11-24
normally, in unix, the /etc/default/login file would be where you deny root logins, but ubuntu doesn't have that file.  it does have a /etc/login.def file which looks to be the equivalent.  try uncommenting out the line 
#CONSOLE        /etc/consoles
rebooting, and see if you can login as root then.

---

### Post by mcduck on 2006-11-24
Ubuntu is configured to use sudo instead of letting users to mess their systems by logging in as root.

I recommend reading this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

