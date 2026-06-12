---
title: "can not download the upgrades"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by Sharimon on 2011-06-01
The message showing like 'Can't download the upgrades", While i am upgrading to 11.04. 

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-2ubuntu5.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-2ubuntu5.2_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.1-2ubuntu5.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.1-2ubuntu5.2_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.1-2ubuntu5.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.1-2ubuntu5.2_all.deb) 404  Not Found [IP: 91.189.92.167 80]


Please help

---

### Post by donut123 on 2011-06-01
Try here 
 [http://www.ultimateeditionoz.com/forum/viewtopic.php?f=32&t=2674&p=17081#p17081](http://www.ultimateeditionoz.com/forum/viewtopic.php?f=32&t=2674&p=17081#p17081)

---

### Post by TBABill on 2011-06-01
Can you try ```
sudo apt-get update && sudo apt-get upgrade
```
 
Disregard, I mis-read your problem the first time.

---

### Post by Handssolow on 2011-06-01
I had this same problem yesterday and today. Update Manager was unable to download these same updates for my 10.10 Maverick, suggesting there was a problem with my Internet connection which there wasn't. It's irritating when my system is falsely blamed in this way.
Anyway "sudo apt-get update && sudo apt-get upgrade" worked.

---

### Post by donut123 on 2011-06-01
> **Handssolow said:**
> I had this same problem yesterday and today. Update Manager was unable to download these same updates for my 10.10 Maverick, suggesting there was a problem with my Internet connection which there wasn't. It's irritating when my system is falsely blamed in this way.
Anyway "sudo apt-get update && sudo apt-get upgrade" worked.
Yes I had that same problem..check internet connection..but i saw the post on Ultimate oz..only I cannot update my vuze
here is my thread..the dudes on Ultmate OZ dont want to help me any longer.....so I came on here 
here is the thread
 [http://ubuntuforums.org/showthread.php?t=1772947](http://ubuntuforums.org/showthread.php?t=1772947)
but I dont want to upgrade it breaks the 2.9.i only want to update Vuze

---

