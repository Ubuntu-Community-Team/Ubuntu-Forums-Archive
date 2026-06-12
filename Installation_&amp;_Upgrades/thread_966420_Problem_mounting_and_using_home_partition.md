---
title: "Problem mounting and using /home partition"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by melat0nin on 2008-11-01
Hello all

I have a /home partition which was created with my previous installation of 8.04.1.

I installed 8.10, instructing the installer to format the system partition (/) and install the new system there.  I also told it to use the existing swap partition for that function.

I didn't tell it to mount my /home partition as /home, because I wasn't sure whether this would nuke all the stuff in there.  I figured I would configure that afterwards, after install.

I'm having a hard time getting my /home partition to actually work.  I added the following to my /etc/fstab file:

```
/dev/sda4 /home ext3 relatime 0 2
```

and it seemed to mount okay, but I get a load of errors when I try to log in.

Stupidly I created a username on the new (8.10) install which is different from the username on the /home folder.  I created 'laurie', while the one on the /home I want to use is 'laurence'.  I promptly created a new user in Ubuntu called 'laurence' with the same password, but I get loads of errors about ICEauthority files and whatnot.  Needless to say it does not work.

I think I have to do something with chown but I'm not sure what.  I am anxious not to lose what's on my /home partition.

Can anyone give me any pointers?  In future, is it safe to tell the Ubuntu installer to mount the partition as /home, without the format box ticked, and all this will be done for me (provided I use the same username, password and system name as the profile on the /home partition)?

Any help would be much appreciated :)

---

### Post by m_l17 on 2008-11-01
> In future, is it safe to tell the Ubuntu installer to mount the partition as /home, without the format box ticked, and all this will be done for me (provided I use the same username, password and system name as the profile on the /home partition)?


I have done this in the past with no problems, just make sure not to check format. But it is always good practice to have a backup just in case things go wrong.

---

