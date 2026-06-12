---
title: "feisty and samba help please"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by rahelvey on 2007-04-15
I have used networking for a few years now. On edgy dapper hoary and only had minor problems with edgy { /// and all } however I am completely unable to setup sharing with xp on feisty. Anyone help?

---

### Post by Abandon on 2007-04-15
sudo apt-get install samba smbclient smbfs

sudo gedit /etc/samba/smb.conf

Change "workgroup" in MSHOME (of whatever is you're workgroupname)

Append at the bottom of smb.conf the following:

[homes]
comment = Personal maps
browseable = no
writeable = yes

Reload Samba with:

sudo /etc/init.d/samba force-reload

followed by adding the windowuser to samba:

sudo smbpasswd -a <username> (i.e sudo smbpasswd -a rahelvey
Than give you're windows password

and that makes:

\\<servername>\<username> in you're filemanager and be done with it. 

Hope this helped you out. :)

---

