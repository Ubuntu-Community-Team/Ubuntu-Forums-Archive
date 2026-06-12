---
title: "Unable to load images from my Apache server"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by kidgrave on 2012-11-05
I have apache up, it's up and working. I am able to create files, but I am however unable to paste files to my /var/www directory. So what can I do to fix this problem?? Here is a screen shot of the error I get when I try to paste files:

[IMG]http://i50.tinypic.com/ephv8p.png[/IMG]

Under "Show More Details", it says:

Error when getting information for file '/home/kidgrave/Pictures/advertised.jpg
': No such file or directory

---

### Post by doktorOblivion on 2012-11-05
This is most likely a group or permissions issue.  Have you tried an:
```

ls -al

```
on both the source and target directories to see if there is a problem with either yet?  If not, bring up a terminal session and perform this command on both directories.  Make sure appropriate permissions or ownership exist on both in order for the file move to work.  If you cannot figure this out post what you see here for others to look further into the issue.

---

### Post by kidgrave on 2012-11-05
> **doktorOblivion said:**
> This is most likely a group or permissions issue.  Have you tried an:
```

ls -al

```on both the source and target directories to see if there is a problem with either yet?  If not, bring up a terminal session and perform this command on both directories.  Make sure appropriate permissions or ownership exist on both in order for the file move to work.  If you cannot figure this out post what you see here for others to look further into the issue.

I'll try that out. I just decided to paste my files elsewhere, where I am able to actually paste them. Now that I have done that I am having another issue; when I go online, I am able to see all my php and index files. However, I am unable to load any type of images, and when I click on images I get this following error:

Forbidden

You don't have permission to access /v7/affiliatesbg.jpg on this server.
Apache/2.2.22 (Ubuntu) Server at [www.animesecret.info](www.animesecret.info) Port 80

Please help, thanks.

---

### Post by doktorOblivion on 2012-11-05
Then you are definitely having permission issues.  Do you know what directories are the issue?  If not, peruse the auth.log:
```

view /var/log/auth.log

```
In this file you should see issues having to do with bad permissions.  Once you figure out what the directory and/or files are that are causing the problem, you can do one of two things.  You may either change the permissions on the directories/files so that the program(s) you are using that are trying to access them have access, like:
```

sudo chmod 755 my_dir

```
Or, give the program access to the group that owns them (by adding it to the appropriate user group).  There are several ways of doing this, e.g. changing /etc/groups directly.

---

### Post by kidgrave on 2012-11-05
> **doktorOblivion said:**
> Then you are definitely having permission issues.  Do you know what directories are the issue?  If not, peruse the auth.log:
```

view /var/log/auth.log

```In this file you should see issues having to do with bad permissions.  Once you figure out what the directory and/or files are that are causing the problem, you can do one of two things.  You may either change the permissions on the directories/files so that the program(s) you are using that are trying to access them have access, like:
```

sudo chmod 755 my_dir

```Or, give the program access to the group that owns them (by adding it to the appropriate user group).  There are several ways of doing this, e.g. changing /etc/groups directly.

I am not sure which files are causing the problem or which directory. I typed what you told me and this is what I got


```


Nov  4 22:39:14 kidgrave-RS482-SB400 mdm[1018]: pam_unix(mdm-autologin:session): session opened for user kidgrave by (uid=0)
Nov  4 22:39:14 kidgrave-RS482-SB400 mdm[1018]: pam_ck_connector(mdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
Nov  4 22:39:19 kidgrave-RS482-SB400 polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session1 (system bus name :1.17 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Nov  4 23:01:59 kidgrave-RS482-SB400 mdm[960]: pam_unix(mdm-autologin:session): session opened for user kidgrave by (uid=0)
Nov  4 23:01:59 kidgrave-RS482-SB400 mdm[960]: pam_ck_connector(mdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
Nov  4 23:02:03 kidgrave-RS482-SB400 polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session1 (system bus name :1.19 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Nov  4 23:09:56 kidgrave-RS482-SB400 sudo: kidgrave : TTY=pts/0 ; PWD=/home/kidgrave ; USER=root ; COMMAND=/usr/bin/apt-get install --reinstall ttf-mscorefonts-installer
Nov  4 23:09:56 kidgrave-RS482-SB400 sudo: pam_unix(sudo:session): session opened for user root by kidgrave(uid=1000)
Nov  4 23:10:33 kidgrave-RS482-SB400 sudo: pam_unix(sudo:session): session closed for user root
"/var/log/auth.log" [readonly] 337L, 42888C

```

---

### Post by BicyclerBoy on 2012-11-05
The OP just needs to copy the file into /var/www/ with sudo cp..

Messing about with the /var/www/ permissions or letting a web server roam all over the filesystem is not a good idea.

You can just launch nautilus with sudo to copy those files over.
I would put all the public access material under /var/www/.

---

### Post by kidgrave on 2012-11-06
> **BicyclerBoy said:**
> The OP just needs to copy the file into /var/www/ with sudo cp..

Messing about with the /var/www/ permissions or letting a web server roam all over the filesystem is not a good idea.

You can just launch nautilus with sudo to copy those files over.
I would put all the public access material under /var/www/.

Is it a good idea to put the files under /home/user/Documents/  ???

---

### Post by doktorOblivion on 2012-11-06
This might help, read this append on the linux forum:
[http://serverfault.com/questions/302447/correctly-setting-up-apache2-permissions-in-var-www-example-com]("http://serverfault.com/questions/302447/correctly-setting-up-apache2-permissions-in-var-www-example-com")

---

