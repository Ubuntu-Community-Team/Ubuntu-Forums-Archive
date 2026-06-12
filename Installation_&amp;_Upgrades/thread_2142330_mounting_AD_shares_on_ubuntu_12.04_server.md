---
title: "mounting AD shares on ubuntu 12.04 server"
date: 2013-05-05
forum: Installation &amp; Upgrades
---

### Post by atm123 on 2013-05-05
hi,
   i had installed cifs-utils and smbfs in my 12.04 server for mounting a win AD  share. also had an entry in the fstab file with a credentials file mapping the username and passwd for the windows AD share.  it was working fine for a few days but stopped working all of a sudden. any help will be appreciated. thanks.

---

### Post by 2F4U on 2013-05-05
As far as I know, you have to configure Samba to join the Active Directory in order to be able to mount a share on the Windows 2012 Server:

[https://help.ubuntu.com/10.04/serverguide/samba-ad-integration.html](https://help.ubuntu.com/10.04/serverguide/samba-ad-integration.html)

---

### Post by darkod on 2013-05-05
Were you mounting the share by IP? Is it possible your AD server IP changed?

Is it possible a firewall on the AD server is blocking the connection now?

To start with, can you ping the AD server where the share is?

---

### Post by atm123 on 2013-05-07
thanks for the replies.  i am sorry, guess i have to make my issue more clear.i have an svn server which is supposed to backup its svn stuff on to a windows 2008r2 file server share from which it goes to a tape library. so first i have to get the svn files from the svn server to the win file server. so thats why i had used  "[COLOR=#333333]//servername/sharename  /media/windowsshare  cifs  username=msusername,password=mspassword,iocharset=utf8,sec=ntlm  0  0"  on the svn server which works. i also added an entry to fstab and it really worked after a couple of reboots automatically. but now all of a sudden i am not able to connect automatically. but the command mentioned above with cifs alone works  when manually used. i was guided by this link: [/COLOR][https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by darkod on 2013-05-07
What if you use //serverIP/sharename? I don't know why, but it could happen that the ubuntu box is not reaching the windows box by name any more. By IP it should always work.

---

### Post by atm123 on 2013-05-07
i am actually using the ip and not the name. any other suggestions you have for mounting as per my requirement?

                                                                               thanks

---

### Post by darkod on 2013-05-07
No, all seems to be correct. As long as the username and password are still correct and active, it should work.
Another small modification I would do is not use the /media mount point. That is where removable media is usually mounted. You can create the same folder in /mnt like /mnt/windowsshare and use that as mount point. It's better to use /mnt than /media for permanent mounts. but it should work even with /media.

---

