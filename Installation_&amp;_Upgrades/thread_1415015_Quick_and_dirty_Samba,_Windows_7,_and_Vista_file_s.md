---
title: "Quick and dirty Samba, Windows 7, and Vista file sharing"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by jdarling on 2010-02-24
I (like quite a few that others that I've seen post here and over on the Windows 7 forums) was having problems getting my Ubuntu 9.10 server system to share files with all of the other systems on my network.  After quite a bit of digging around and some trial and error I've found a solution that I can reproduce file sharing with every time (I've done clean installs and followed my own directions on 3 different boxes just to validate that I had it right).

I'm making the assumption that you already have a system setup and that you already know what shares you want to setup.

Just in case, you will want to make sure you have all of the following packages setup:
```
sudo apt-get install samba smbclient smbfs ntp ntpdate
```

Once samba is installed you need to edit the smb.conf file:
```
sudo vi /etc/samba/smb.conf
```

1st find the line that says "security = ???" and change it so it reads:
```
security = share
```

Next add in your share's as follows (making changes where appropriate of course):
```
[share name]
path = /path/to/file
guest ok = yes
writeable = yes
only user = no
username = YourUserName
hide dot files = no
```

Then restart/reload samba:
```
sudo /etc/init.d/samba force-reload
```

I'm sure that this isn't the one size fits all solution since it basically disables security on your shares, forces you to have to redefine user account per share, and isn't exactly straight forward, but I've had NO issues with sharing files between Windows 95->Window 7, Mac OSX Leopard and Ubuntu doing things this way.

I wouldn't use it in an open network, but behind a firewall and without (or with a really good) wireless your in limited problem area.

Hope this helps someone, and any better ideas or ideas on how to make the force user global I'd love to hear them.

 - Jeremy

---

