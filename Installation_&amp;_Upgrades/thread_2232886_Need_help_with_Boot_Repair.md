---
title: "Need help with Boot Repair"
date: 2014-07-04
forum: Installation &amp; Upgrades
---

### Post by bcollins247 on 2014-07-04
Hello,

I'm running ubuntu 14.04 on my laptop and today my boot became corrupted.  I have tried using the boot repair program from a LiveCD to no avail.  I would try to just grab my documents and to a full reinstall, but the hard drive won't let me in (even after I give my admin password).  So I'm kinda stuck at the moment.  

[http://paste.ubuntu.com/7749054](http://paste.ubuntu.com/7749054)

---

### Post by oldfred on 2014-07-09
It looks like an encrypted install. So without correct passphrase no data will be accessible. 
With encryption really good backups are about the only way to recover data.

As Boot-Repair suggested:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

       Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

