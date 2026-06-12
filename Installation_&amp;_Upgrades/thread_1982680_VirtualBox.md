---
title: "VirtualBox"
date: 2012-05-19
forum: Installation &amp; Upgrades
---

### Post by DoctorVell on 2012-05-19
FIRST OFF, if this is in the wrong place, please someone let me know where it is supposed to go and then I will repost the question there.

1) I have VirtualBox installed with Windows XP as the OS I use.

2) It works perfectly fine, but I am trying to have a shared folder between the Ubuntu and the VirtualBox XP disk.

3) I have it set up as shared, but when I try in the Windows side, it let's me Map the drive, but then when I click on where it is, I get username and password prompt.  What do I need to do to make sure I can read/write this folder within XP.


I am using Ubuntu 12.04 btw...

Thanks :)

---

### Post by wilee-nilee on 2012-05-19
> **DoctorVell said:**
> FIRST OFF, if this is in the wrong place, please someone let me know where it is supposed to go and then I will repost the question there.

1) I have VirtualBox installed with Windows XP as the OS I use.

2) It works perfectly fine, but I am trying to have a shared folder between the Ubuntu and the VirtualBox XP disk.

3) I have it set up as shared, but when I try in the Windows side, it let's me Map the drive, but then when I click on where it is, I get username and password prompt.  What do I need to do to make sure I can read/write this folder within XP.


I am using Ubuntu 12.04 btw...

Thanks :)

Did you set the share as automount  and full access, not sure but it may need to be setup from the admin in XP, mine work every time. I also make sure my host is in the virtual as a user

---

### Post by DoctorVell on 2012-05-20
> **wilee-nilee said:**
> Did you set the share as automount  and full access, not sure but it may need to be setup from the admin in XP, mine work every time. I also make sure my host is in the virtual as a user

I got it figured it out, I forgot to do a share folder on the Ubuntu side and now it works perfectly fine.

---

