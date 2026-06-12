---
title: "since upgraded to feisty..."
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by mad chey on 2007-04-21
i for some reason no longer mount a shared folder from my husbands pc on startup

i can go into places>network  and i see his pc, i click on that and i see the folder in question and i can access it and copy from and play music from it, exactly as before

but the entry in fstab is no longer correct apparently

sudo mount -a        gets me the following error message


16139: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed


i can ping his pc, ive tried using his pcs name and its IP addy all to no avail, ive tried googling it but i always seem to come up with solutions to connecting to windows pcs

my pc is now running feisty, his is running dapper, all was good till i upgraded

any suggestions greatly appreciated

thanks

---

### Post by darrenm on 2007-04-21
Access denied basically means you aren't supplying the correct username or password. Feisty shouldn't change that. Are you putting the username and password into /etc/fstab ?

Try using smbclient to connect to the share. ```
smbclient //hostname/share password -U username
```

If there is no password set up then the share on the Dapper computer needs to have the following in /etc/samba/smb.conf for that share:

read only = no
public = yes
security = share
guest ok = yes

and the directory that the share is trying to access needs to have read permissions for the user you are connecting as

Hope this helps. Need more info about your set up if you still can't get it working :)

---

### Post by mad chey on 2007-04-21
scratch that, did a restart (probably the 8th one today) and now its mounting it fine, bizzare and i have no explanation

sorry to have bothered you guys thanks for you help tho

---

