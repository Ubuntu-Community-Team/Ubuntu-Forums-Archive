---
title: "Weird Alien chown Error"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by RMOP on 2008-08-02
I previously used this command to update my StarOffice installation (see closed thread "StarOffice 8.0 Update Fails" [http://ubuntuforums.org/showthread.php?t=734121](http://ubuntuforums.org/showthread.php?t=734121)[PHP][/PHP]). Now, in attempting to install the latest SO update, I get the cryptic message shown below. I'm baffled.

rmop@UBUNTU:/MyDirectory/120184-15/rpms$ sudo alien -i --scripts /MyDirectory/120184-15/rpms/*.rpm
chown: changing ownership of `staroffice-base-8.0.11//opt/staroffice8': Operation not permitted
failed chowning /opt/staroffice8 to 0:0: Illegal seek at /usr/share/perl5/Alien/Package/Rpm.pm line 246, <GETPERMS> line 1.
rmop@UBUNTU:/MyDirectory/120184-15/rpms$

Sounds like a permissions issue, but I don't know why or what to do.

Help?

---

