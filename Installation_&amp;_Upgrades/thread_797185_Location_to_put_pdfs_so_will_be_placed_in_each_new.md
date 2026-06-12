---
title: "Location to put pdfs so will be placed in each new account"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by John Read on 2008-05-17
Hi everyone,

I want to find the location where I can place several documents (in pdf format) so that when I create new accounts these documents will appear on the Desktop of each of these new accounts.

Any help much appreciated.

Regards,

John R.

---

### Post by iaculallad on 2008-05-17
An Option: How about creating a folder in your /home folder and sharing it through NFS or SMB? This would give access to users using your PC or on the network.

~ Not linked on the Desktop.

---

### Post by John Read on 2008-05-18
Thanks for the suggestion iaculallad,

I'm installing Ubuntu onto computers for refugees without any network. Each PC gets 4 accounts (user01 to user04) & it's a bit of a pain having to put the pdf files onto the Desktop of each account.

I seem to remember that you could put stuff into a skeleton directory, but perhaps that was back in my Microsoft Windows days.

Regards,

John R.

---

### Post by cdtech on 2008-05-18
It's the /etc/skel directory. Anything within this directory gets copied to the new user directory.

---

### Post by John Read on 2008-05-18
Thanks a lot cdtech. That'll save me some time when I'm setting them up.

regards,

John R.

---

### Post by cdtech on 2008-05-19
No prob, good luck.

---

