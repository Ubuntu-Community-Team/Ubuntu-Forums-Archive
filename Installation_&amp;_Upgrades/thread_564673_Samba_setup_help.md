---
title: "Samba setup help"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by rkdyer1 on 2007-10-01
I have installed samba on my 7.04 box and can see the shares from my windows xp home box, however whenever I try and connect to the Ubuntu box from xp it continually asks me for my password.

Here is my smb.conf file

>>

# Global parameters
[global]
       workgroup = MSHOME
       netbios name = SAMBA
       server string = Samba Server %v
       map to guest = Bad User
       log file = /var/log/samba/log.%m
       max log size = 50
       socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
       preferred master = No
       local master = No
       dns proxy = No
       security = user
       encrypt passwords = yes

# Share
[Data]
       path = /FILESERVER
       read only = No
       create mask = 0777
       directory mask = 0777

>>

Not sure where to go from here.

---

### Post by Buickman on 2007-10-01
Did you run smbpasswd for root and your user name?

smbpasswd -a root
smbpasswd -a username

Here's a good howto;

[http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10](http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10)

Works for Feisty as well.

---

### Post by rkdyer1 on 2007-10-01
What password do I use for the root user in samba?  My linux user password or my Windows administrator password?

---

### Post by rkdyer1 on 2007-10-01
So I ran these commands

$ sudo smbpasswd -a root
NEW SMB password <my ubuntu logon password>

then restarted samba and now I can log into the shares from my XP box using the username root and my Ubuntu logon password, however I cannot logon with my XP logon name and password.  I thought I already added my XP logon as a linux user and made a samba user and pasword for it, how would I check that?

Rick

---

### Post by Buickman on 2007-10-01
Did you run 'sudo smbpasswd -a <yourusername>?

Read through the link I posted. It hasn't failed me yet. I start on page 3 and skip quota, then the meat of it is on page 4.

---

### Post by rkdyer1 on 2007-10-01
Yes, I ran the command to add the samba user and password for my XP logon.  I also ran through the configuration you sent in the link, and I was able to see the shares in XP, however could not log in still.

Rick

---

