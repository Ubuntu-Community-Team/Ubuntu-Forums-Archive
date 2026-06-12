---
title: "Root Password"
date: 2005-10-10
forum: Installation &amp; Upgrades
---

### Post by johnpmurphy on 2005-10-10
I have installed Ubuntu from an ISO image and at no time have I been asked to set up a root password.  I don't know if that is deliberate, I just get asked to set up a single user.  This makes it difficult to change folder permissions etc.
Can anyone tell me how I can either set a root password or discover what the default root password is.  I am a newbie, in case yo hadn't worked it out.

thanks

John

---

### Post by heimo on 2005-10-10
This should answer it:
[https://wiki.ubuntu.com/RootSudo/](https://wiki.ubuntu.com/RootSudo/)

---

### Post by johnpmurphy on 2005-10-10
Thank you, got that.  The reason this came up is that my Windows box on the network could not access folders on my Ubuntu box, saying I did not have premission, refer to sys admin etc.  However when I tried to change the permissions it said they were owned by "root".  I tried running the File Manager as "root" and put in the user password, which it promptly rejected.
  Am I missing some trick here,  All I am trying to do is to make a folder on the Liuux box visible from the Windows box.  I have activated both Samba and NFS.
  So far I have been unable to setup a networked drive on either system as I want to use my old computer as a back up filestore.
  It is a shame that there is not a simple graphic tool accessible from Gnome that even idiots like me can use to set up a home network (if windows can do it why can't the geniuses behind Ubuntu do something better)

  Any ideas

Many thanks


John

---

### Post by heimo on 2005-10-10
So you have configured samba?
[https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba)
[http://ubuntuguide.org/#installsamba](http://ubuntuguide.org/#installsamba)

I don't know much about that - I use ssh / scp to share between my computers (over insecure wan/internet).

Some settings are in System -> Administration -> Shared Folders:
[http://ubuntuforums.org/showpost.php?p=300540&postcount=9](http://ubuntuforums.org/showpost.php?p=300540&postcount=9)

---

