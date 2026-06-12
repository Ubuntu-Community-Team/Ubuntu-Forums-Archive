---
title: "Problems with installing of the openssh-server"
date: 2019-02-09
forum: Installation &amp; Upgrades
---

### Post by Forecaster on 2019-02-09
Hi!

We installed 16.04 Ubuntu into LattePanda minicomputer ([https://www.lattepanda.com/blog-tag/linux](https://www.lattepanda.com/blog-tag/linux)) and wanted to install ssh server for remote access. 

What we received after our attempt to do it:
apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 openssh-server : Depends: openssh-client (= 1:7.1p1-4)
                  Depends: openssh-sftp-server but it is not going to be installed
                  Recommends: ssh-import-id but it is not going to be installed [COLOR=#000000]E: Unable to correct problems, you have held broken packages.

[/COLOR]

---

### Post by dmnur on 2019-02-09
Show your **/etc/apt/sources.list**. Also files in **/etc/apt/sources.list.d** if it's not empty.

---

### Post by Forecaster on 2019-02-09
Thank you about your good answer. I will do it at Monday. I worked all day today with Ubuntu and LattePanda.

---

### Post by Forecaster on 2019-02-12
1) The source from FTP server with LattePanda apt sources 
[ftp://194.44.29.164/pub/publications/ProblemWithAPT/LattePandaMiniComp/](ftp://194.44.29.164/pub/publications/ProblemWithAPT/LattePandaMiniComp/)
2) The source from FTP server with other Ubuntu computer
[ftp://194.44.29.164/pub/publications/ProblemWithAPT/OtherMiniGoodComp/](ftp://194.44.29.164/pub/publications/ProblemWithAPT/OtherMiniGoodComp/)

---

### Post by Forecaster on 2019-02-12
Thank you!
This difficult task is fully solved - 
 service sshd status
&#9679; ssh.service - OpenBSD Secure Shell server
   Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
   Active: active (running) since &#20108; 2019-02-12 17:31:28 CST; 9min ago
 Main PID: 15622 (sshd)
   CGroup: /system.slice/ssh.service
           &#9492;&#9472;15622 /usr/sbin/sshd -D

2&#26376; 12 17:31:28 admin systemd[1]: Started OpenBSD Secure Shell server.
2&#26376; 12 17:31:28 admin sshd[15622]: Server listening on 0.0.0.0 port 22.
2&#26376; 12 17:31:28 admin sshd[15622]: Server listening on :: port 22.
2&#26376; 12 17:31:56 admin sshd[15630]: Accepted password for admin from 192.168.7.21 port 39084 ssh2
2&#26376; 12 17:31:56 admin sshd[15630]: pam_unix(sshd:session): session opened for user admin by (uid=0)

How it was solved?
I have used this web-page fpr solving difficult task:
[h=3]**Method 2: Use Aptitude**[/h] **Aptitude **is an alternative of **apt-get **which  you can use as a higher-level package manager. You can use it to try  and install your package with it, instead of apt-get, but first you need  to install **aptitude. **
 
[LIST=1]
[*]Press simultaneously the **Ctrl, Alt, **and **T **keys on your keyboard to open a
[*]Type in **sudo apt-get install aptitude **and press **Enter **to execute the command.
[*]Type in **sudo aptitude install PACKAGENAME, **where PACKAGENAME is the package you&#8217;re installing, and press **Enter **to  execute it. This will try to install the package via aptitude instead  of apt-get, which should potentially fix the unmet dependencies issue.

Regards,
Serge
[/LIST]

---

### Post by Forecaster on 2019-02-12
Web-page - [https://appuals.com/fix-unmet-dependencies-error-ubuntu/](https://appuals.com/fix-unmet-dependencies-error-ubuntu/)

---

