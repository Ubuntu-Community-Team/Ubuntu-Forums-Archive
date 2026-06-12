---
title: "Server 10.04 LTS login problem"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by setchp on 2011-08-11
I am responsible for around 20 ubuntu servers in schools. I have been upgrading a school to Ubuntu Server 10.04 LTS. The setup is very simple, just ssh server, and samba server.

Upgrade involves completely new disks, with just a transfer of files after setup from the old disks.

All goes well until I create the samba user/passwd pairs. After the next and all subsequent boots logging into the server causes a pause of approx 2-3 mins after typing in the password.

Also up to the first reboot after entering the samba info, I can access the shares via smbclient, but after the reboots this also takes a long time.

I have now done 2 complete reinstalls reformatting the / drive partition, problem comes back.

I wonder if anyone else has seen this problem.

Many thanks

SteveP

---

### Post by setchp on 2011-08-11
Thanks to those who viewed this problem.

Looks like I've fixed it. The fault seems to be wins server issues. Turning it off in smb.conf cleared the problem, although I'm still unclear why it should interfere with logging into the server itself.

SteveP

---

