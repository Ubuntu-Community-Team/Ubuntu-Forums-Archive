---
title: "Unable to mount HDD &amp; usb"
date: 2012-11-06
forum: Installation &amp; Upgrades
---

### Post by jeffbilling on 2012-11-06
I have just upgrade to Ubuntu 12.10 and I now receive this error message when trying to access external drives
What do I do:confused::confused:

---

### Post by 2F4U on 2012-11-07
Can you check whether the folder /media/jeffrey exists and what the permissions are?

[http://askubuntu.com/questions/202560/cant-mount-any-partition-due-to-usb-adding-read-acl-for-uid-1000-to-media-e](http://askubuntu.com/questions/202560/cant-mount-any-partition-due-to-usb-adding-read-acl-for-uid-1000-to-media-e)
[http://askubuntu.com/questions/202630/cant-mount-any-partition-acl-error](http://askubuntu.com/questions/202630/cant-mount-any-partition-acl-error)

---

### Post by jeffbilling on 2012-11-07
Thanks again 2F4U.
I spent a couple of hours searching for this answer but obviously I am not using the right keywords.
I pasted 'sudo mkdir /media/${USER}' into terminal and Bingo everything seems fine. You're a diamond!!!
Jeff

---

