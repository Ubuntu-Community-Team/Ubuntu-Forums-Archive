---
title: "SMB problems in 8.10"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by Philio on 2008-11-25
I've installed 8.10 on 2 PC's to see what the desktop version is like. I Installed identical packages on both.

If I go to Places -> Network -> Windows Network neither computer show any network computers.

If I go to Places -> Connect to a server and try and connect to a windows share, I get the message 'Cannot display location "smb://computername/" No application is registered as handling this file'

However this location is accessible via Firefox!

Seams like SMB is gimped in Intrepid (like many other things), yet another poorly tested new version which doesn't work properly.

Anyone else experiencing any of these issues?

---

### Post by DieB on 2008-11-25
with ip-adresses it works for me

---

### Post by ubrox on 2009-01-07
Same problem in 8.10. Was working fine before I moved to 8.10.

Edit: Saw another post - this error comes up if you fail to give the name of the share to mount / connect to. If you provide a share name, it is all good. If you dont know the share name, you have to use Places->Network or use "smbclient -L <IP or name> -U <username> tp see list of shares.

---

