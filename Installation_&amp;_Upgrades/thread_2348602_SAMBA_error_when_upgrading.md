---
title: "SAMBA error when upgrading"
date: 2017-01-05
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2017-01-05
Just trying to update and upgrade my wife's la[ptop - HP Pavillion g series, image 4.2.0-41 and getting an error message.

```
Use 'apt-get autoremove' to remove them.
Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up samba (2:4.3.9+dfsg-0ubuntu0.15.10.2) ...
Job for smbd.service failed because the control process exited with error code. See "systemctl status smbd.service" and "journalctl -xe" for details.
invoke-rc.d: initscript smbd, action "start" failed.
dpkg: error processing package samba (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Tried the autoremove and same error message.

Any ideas, please?

---

### Post by Morbius1 on 2017-01-05
> Job for smbd.service failed because the control process exited with error code. See "systemctl status smbd.service" and "journalctl -xe" for details.
invoke-rc.d: initscript smbd, action "start" failed.
dpkg: error processing package samba (--configure):
 subprocess installed post-installation script returned error exit status 1
This is just a guess but that error message has happened to so many people when they updated to the latest version of samba that it may be the cause here as well.

Look at /etc/samba/smb.conf and search for a line that looks like this:
> security = share
Either change **share** to **user **or just delete the line which will set it to the default.
Then restart smbd:
```
sudo service smbd restart
```
In the past samba would log an error telling you that share level security was deprecated then ignore the line in smb.conf. With the latest version of samba they got persnickety and will actually prevent smbd from running.

---

### Post by Jonners59 on 2017-01-05
> **Morbius1 said:**
> This is just a guess but that error message has happened to so many people when they updated to the latest version of samba that it may be the cause here as well.

Look at /etc/samba/smb.conf and search for a line that looks like this:

Either change **share** to **user **or just delete the line which will set it to the default.
Then restart smbd:
```
sudo service smbd restart
```
In the past samba would log an error telling you that share level security was deprecated then ignore the line in smb.conf. With the latest version of samba they got persnickety and will actually prevent smbd from running.

Thanks Morbius1
No line security=share or anything like it

Have this though in Global
  usershare owner only = false
and this in Misc.
  usershare allow guests = yes
and this in Share Definitions
  usershare_acl=Everyone:F,

Could they be the cause?

---

### Post by Jonners59 on 2017-01-05
OK, went in to the config file again and changed all the =y to =yes and the error message disappeared, but still no sign of upgrades though.....

---

### Post by Jonners59 on 2017-01-06
Not sure why one of my posts triplicated itself, but anyway....

So as per I did not find that specific line nore anything like it.  What I did do was change any =y to =yes and restarted samba.

I then did all the cleaning, ```
sudo apt-get clean
```, autoremove, etc and it started to work and the warning disappeared.  Hopefully that's the last of it.

---

