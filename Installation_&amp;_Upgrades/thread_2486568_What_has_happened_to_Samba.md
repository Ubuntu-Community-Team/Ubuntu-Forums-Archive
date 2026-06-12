---
title: "What has happened to Samba??"
date: 2023-05-04
forum: Installation &amp; Upgrades
---

### Post by KDMerrill on 2023-05-04
Greetings All.  I had to do a fresh install due to system corruption  after an upgrade, so I did a factory fresh new install of 20.04.6.  I  cannot get Samba to work for the life of me, has something changed? If I  try to do a 'Local Network Share' via the GUI, when I try to share ANY  folder I get thse errors:

'net usershare' returned error 255: [2023/05/04 11:48:32,  0] ../../lib/util/debug.c:1100(reopen_one_log)
  reopen_one_log: Unable to open new log file 'MP3/log.net': No such file or directory
net usershare add: share name /media/kevin/storage/mp3 contains invalid characters (any of %<>*?|/\+=;:",)


I can't seem to find any GUI-based interface, and I could have sworn  there used to be one.  Even with a very simplified smb.conf I still  can't get a share to show up on our home network for our windows laptops  to see and access.  Samba has worked for me for 10+ years ans I've  always loved it' simplicity....what in the world happened???

Kevin in VA

---

### Post by TheFu on 2023-05-04
Most of the GUI tools broke.
The best way to setup Samba/CIFS is to modify the /etc/samba/smb.conf file.
Beware that Windows 7, 10, 11 have all mucked with their default CIFS settings. Some aren't included in the defaults.

If you'd like help, run the following command and post the output wrapped in forum code tags:
```
testparm -s
```
Then someone knowledgeable might be able to help.

Also, please list the exact clients being run for these connections.  This is really to know which version of the SMB/CIFS protocol needs to be supported.  Support for old versions are not enabled by default in 20.04 and later, so older clients will have connection issues. There are ways to allow those clients, but doing that will impact performance and security.

---

### Post by KDMerrill on 2023-05-05
Appreciate any guidance I can get:   testparm - s yields the following:

> Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed

Server role: ROLE_STANDALONE

# Global parameters
[global]
    log file = /var/log/samba/log.%m
    logging = file
    max log size = 1000
    panic action = /usr/share/samba/panic-action %d
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    usershare allow guests = Yes
    usershare owner only = No
    idmap config * : backend = tdb

[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[MP3]
    comment = MP3 Library
    guest ok = Yes
    guest only = Yes
    path = /media/kevin/Storage/MP3
    read only = No

[Share-Docs]
    comment = Shared Documents
    guest ok = Yes
    guest only = Yes
    path = /media/kevin/Storage/Share_Docs
    read only = No

[Photos]
    comment = Shared Photos
    guest ok = Yes
    guest only = Yes
    path = /media/kevin/Photo_Partition/photos
    read only = No


The client laptops are Windows 10 & 11....and we used to be able to access the Samba shares just by navigating to them across the network using Windows File Explorer.  They do not even show up in Windows File Explorer any longer, and when we navigate to the Ubuntu machine (Joker), it doesn't show any shared folders.

---

### Post by Morbius1 on 2023-05-05
[1] You have disabled guest access to your samba server.

Not sure how this can happen on a new install but you are missing a [global] setting that allow guest access: ```
map to guest = Bad User
```

Add that you your smb.conf - under the workgroup = WORKGROUP line is where I would but it.

[2] All of your shares are invisible to any client machines because of your mount points: /media/kevin/XXXX

Only kevin can gain access to those mount points so if you want to keep them that way make the client user appear to be kevin by adding a "force user = kevin" to your share definitions. Like this:
> [MP3]
comment = MP3 Library
guest ok = Yes
guest only = Yes
path = /media/kevin/Storage/MP3
read only = No
**[COLOR="#B22222"]force user = kevin[/COLOR]**
After the changes restart smbd:
```
sudo service smbd restart
```

Win10/11 will still not be able to "discover" your samba server however without enabling SMBv1 on both machines which is not recommended. WHat I suggest is:

Making sure avahi is intstalled on the Samba server:
```
sudo apt install avahi-daemon
```
ANd connecting to the server from win10/11 explicitly in Explorer:
```
\\hostname.local
```
Where hostname is the Linux samba server host name - and don't forget the .local at the end.

[COLOR="#0000CD"]*Note: THis gets easier in Ubuntu 22.04 since discovery will be automatic with the addition of the wsdd package in Linux.*[/COLOR]

THe Linux client has too many bugs for that to work so you will have to access the shares by hostname and share name in the file manager like this:
```
smb://hostname.local/MP3
```

---

### Post by TheFu on 2023-05-05
A few things ... 

The way that MS-Windows deals with browsing changed drastically in Win10 and later.  They dropped support for nmbd, which is how samba browsing worked the last 25 yrs.  I think some form of mDNS is used now, but don't know how to enable it. think a new package has to be installed and enabled. Some other samba-related posts in these forums probably spells it out.

You can enter the shares as //1.2.3.4/MP3 ... does that work?  1.2.3.4 needs to be the IP address for the samba server or the {hostname.local} if avahi is running.

If the file systems mounted under /media/kevin aren't native Linux (ext4). Some other non-Linux file systems complicate this, so if exFAT or NTFS are used, you'll need to setup the mount options manually for those to work.

I've never used guest accounts.  I'd remove "guest only" settings.

To my knowledge, the **smbpasswd** tool must be used to create a password for the users to access any shares.  Try:
```
smbpasswd -a kevin
```

Win7 supports Samba 2.1, so some later version would be used for Win10/11, but I don't know which versions they support. Just start by setting the minimum samba version to 2.1 in the smb.conf file. In the Global section, 
```
; This is for the smb server; 
   min protocol = SMB2

```

Any changes to smb.conf requires restarting the daemon. Don't forget that.

---

### Post by KDMerrill on 2023-05-07
THIS....THIS right here is why I love the Linux Community so much.  I  had worked through trial-and-error to perfect my smb.conf file 8+ years  ago, and my Ubuntu machine was so perfectly stable that I hadn't looked  at it in literally YEARS.  when my install became corrupted, and I  couldn't even access my vital config files (fstab and smb.conf) before  rebuilding my machine from scratch, I searched through a mountain of  thumb drives and CDs and couldn't find backups of those 2 files  anywhere.

Your EXPERT advice, pointing me to the obvious problems  right before my eyes made it all come back with some actual  clarity.....and now my shares are working just as they used to.

[COLOR=#0000ff]**[SIZE=7]THANK YOU !!!!![/SIZE]**[/COLOR]

---

