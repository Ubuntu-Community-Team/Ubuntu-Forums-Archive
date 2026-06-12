---
title: "Help with odd Samba problem please!"
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by wasafiri on 2006-07-26
I just installed Ubuntu 6.06 on a machine here. I use it for a fileserver. I recently purchased a brand spanking new 400gb HD, hence the installation of Ubuntu--wanted to move over from Vector Linux.

Set it up, formatted all the drives Ext3.

This is my Fstab--

> proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /storage/hda1   ext3    defaults        0       0
/dev/hdc5       none            swap    sw              0       0
/dev/hdc6       /storage/hdc6   ext3    defaults        0       0
/dev/hdd1       /storage/hdd1   ext3    defaults        0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


so I installed Samba on it-- 

sudo apt-get install samba
sudo apt-get install smbfs

I configured Samba according to this tutorial over at Howtoforge: 

[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

I made especially sure to follow its instructions for adding users and then adding those users to the Samba password database. I did, however, modify their smb.conf to my liking.

So, ta-da, my new fileserver is all set up. I have three shares going--

/storage/hda1,
/storage/hdc6,
/storage/hdd1.

Now here's the problem (kudos if you stayed this far).

I can, using my WinXP machine, access *all* three shares. However, I can create new files and folders, and add/delete files only on *two* shares--/storage/hdc6 and /storage /hdd1. With these two shares, I can do *anything* from my XP box!

However, I cannot do *anything* on /storage/hda1 except browse. Can't add new files, can't move files there, *nothing*.

It will return the error "Access is denied."

Any idea why?

If it helps, here is my /etc/samba/smb.conf file:

> [global]
   workgroup = APARTMENT
   netbios name = Eunicity
   server string = Samba server

   passdb backend = tdbsam
   security = user
   encrypt passwords = yes
   username map = /etc/samba/smbusers
   smb passwd file = /etc/smbpasswd
   name resolve order = wins bcast hosts
   domain logons = yes
   preferred master = yes
   wins support = yes

   # Default logon
   logon drive = O:
   # logon script = scripts/logon.bat
   logon path = \\Eunicity\profile\%U


   # Useradd scripts
   add user script = /usr/sbin/useradd -m %u
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usermod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000


   # sync smb passwords woth linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
   passwd chat debug = yes
   unix password sync = yes
   # set the loglevel
   log level = 3


[Storage]
   comment = Storage
   valid users = sherlock, ishmael
   path = /storage/hda1
   read only = no
   writable = yes
   browsable = yes
   workgroup = APARTMENT
   netbios name = Eunicity
   server string = Samba server

[Backup]
   comment = Backup
   valid users = sherlock, ishmael
   path = /storage/hdd1
   read only = no
   writable = yes
   browsable = yes
   workgroup = APARTMENT
   netbios name = Eunicity
   server string = Samba server

[Temp]
   comment = Temporary
   valid users = sherlock, ishmael
   path = /storage/hdc6
   read only = no
   writable = yes
   browsable = yes
   workgroup = APARTMENT
   netbios name = Eunicity
   server string = Samba server

[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   admin users = Administrator
   valid users = %U
   read only = no
[profile]
   comment = User profiles
   path = /home/samba/profiles
   valid users = %U
   create mode = 0600
   directory mode = 0700
   writable = yes
   browsable = no

Any ideas what I'm doing wrong, please let me know, thanks!

---

### Post by simonn on 2006-07-26
Permissions on /storage/hda1.

---

### Post by wasafiri on 2006-07-26
I did a chmod 776 /storage/hda1, that did not seem to work. Other suggestions?

---

### Post by simonn on 2006-07-26
Try chmod 777.

---

