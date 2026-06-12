---
title: "Questions Aboout Failed mysql Installation (20.04)"
date: 2020-05-26
forum: Installation &amp; Upgrades
---

### Post by bilkay on 2020-05-26
This is a new installation (not an upgrade). The OS runs from a USB thumbdrive (32G). I installed mysql-client, and then tried to install mysql-server but the installation failed. Here's the error.log:

[https://paste.ubuntu.com/p/zhVbd5n75r/](https://paste.ubuntu.com/p/zhVbd5n75r/)

A couple of deviations are the /var and /tmp directories are links to directories on a harddrive (to avoid excessive read/write to the thumbdrive). The ownership and permissions of the linked-to directories are the same as original. **Correction**: /var was **not** linked!

From the error.log file:
```
2020-05-26T18:41:56.297387Z 0 [Warning] [MY-011810] [Server] Insecure configuration for --pid-file: Location '/tmp' in the path is accessible to all OS users. Consider choosing a different directory.
```
Not sure why this comes up as the actual /tmp directory has permissions "drwxrwxrwt" with root:root ownership.

From the error.log file:
```
2020-05-26T18:41:06.571075Z 6 [Warning] [MY-010453] [Server] root@localhost is created with an empty password ! Please consider switching off the --initialize-insecure option.
```
How do I turn it off? If I don't and successfully install with no root password, can I then run mysql as root with the command "mysql -u root"?

From the error.log file:
```
2020-05-26T18:41:55.732794Z 0 [ERROR] [MY-011300] [Server] Plugin mysqlx reported: 'Setup of socket: '/var/run/mysqld/mysqlx.sock' failed, can't create lock file /var/run/mysqld/mysqlx.sock.lock'
```
Is this a result of having /var as a linked directory (**Correction**: It's **not**)? I'd rather not, but I could create a couple of harddrive partitions and mount them on /var and /tmp.

---

### Post by bilkay on 2020-05-26
I tried doing apt-get reinstall mysql-server and it failed due to a failed dependency with mysql-server-8.0. Trying to install that failed too. When I try to 'service mysql stop' and 'service mysql start', it refers to 'systemctl status mysql.service' which returns;
```
May 26 17:07:37 Jupiter systemd[1]: mysql.service: Scheduled restart job, restart counter is at 5.
May 26 17:07:37 Jupiter systemd[1]: Stopped MySQL Community Server.
May 26 17:07:37 Jupiter systemd[1]: mysql.service: Start request repeated too quickly.
May 26 17:07:37 Jupiter systemd[1]: mysql.service: Failed with result 'exit-code'.
May 26 17:07:37 Jupiter systemd[1]: Failed to start MySQL Community Server.
```
i tried waiting a while between stop and start, but it made no difference.

---

### Post by bilkay on 2020-05-26
This is disheartening!

---

### Post by bilkay on 2020-05-26
FYI, I anticipated problems with this so I cloned the thumbdrive before starting the mysql installation.

---

### Post by SeijiSensei on 2020-05-27
> Not sure why this comes up as the actual /tmp directory has permissions "drwxrwxrwt" with root:root ownership.
Those permissions do grant full access to all users as the MySQL complaint indicates.

On my system, /var/run is a symbolic link to /run.  It is owned by root:root with the usual drwxr-xr-x permissions.  /run and /run/lock are temporary filesystems that exist only in memory and are created at each boot.  If you type "mount" at the prompt, do you have

```
tmpfs on /run type tmpfs (rw,nosuid,nodev,noexec,relatime,size=808796k,mode=755)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)

```

I wouldn't mount a hard drive partition as /var myself.  Let it stay on the USB device.  

14.04 reached its end-of-life in 2019. Do yourself a favor and install a copy of 20.04 which will be supported for the next five years.

Since I limit access to my database servers to the localhost interface, I rarely use passwords. So, yes, you can install a copy with no password and just use "mysql -u root".

---

### Post by bilkay on 2020-05-27
> Those permissions do grant full access to all users as the MySQL complaint indicates.
Those are the permissions for every /tmp I've seen. All users have to have access to /tmp. The "t" bit means that only the owner of something written there can delete it or rename it.

>  14.04 reached its end-of-life in 2019. Do yourself a favor and install a  copy of 20.04 which will be supported for the next five years.
Not sure where that came from. This is dealing with 20.04.

---

### Post by SeijiSensei on 2020-05-27
From your profile:

> Distro Ubuntu 14.04 Trusty Tahr

---

### Post by bilkay on 2020-05-27
> **SeijiSensei said:**
> From your profile:

I guess I should update that.

---

### Post by bilkay on 2020-05-28
I reverted back to my pre-attempt clone and tried installing mysql-server without installing mysql-client first. This time, I got an error saying a temporary file couldn't be written and the installation failed. SO I removed the simlink to /tmp and put /tmp back to its original state. Then mysql-server installed with no errors.

All is now well. Funny that none of the other installations had a problem with a simlinked /tmp directory.

---

