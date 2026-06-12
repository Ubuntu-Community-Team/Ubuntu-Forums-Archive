---
title: "cant install 8.04 from 7.10"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by pwmarcotte on 2008-05-17
when i use the update manager to upgrade from 7.10 to 8.04, i receive a message to check my internet connection.  obviously my network and internet connect are working alright because i can write this post.  can someone assist an ubuntu noob?

---

### Post by Sef on 2008-05-17
Could be that there is a problem with the repositories, so wait a few hours then try again.

---

### Post by pwmarcotte on 2008-05-17
this issue has been occurring for approx 1.5 weeks for me.  there are a few security updates that i can not download and update that i see in the update manager.  i can also install any other new updates when they become available, except for the three updates.

---

### Post by grannyw on 2008-05-17
bug???
or
system corruption???

Dont you want to try a fresh installation?

---

### Post by pwmarcotte on 2008-05-17
thats what i was afraid of was to have to do a clean install.  the thing is im not very good with linux and i have to constantly ask the same friend for advice.  i dont want to get on his nerves by abusing the privilege.  he help me set up several items to assist me in creating my first website.  i dont want to loose all that work.  i did burn an iso of 8.04.  when i reboot and the cd starts, it doesnt offer the option to update the current version or something of the such.  i heard there were other ways to update my system manually, which i have seen and tried.  to no avail.

---

### Post by cdtech on 2008-05-17
I had the same problem with my upgrade. For some reason the server for a certain repository is not functioning properly, so I had to edit mine and remove the us. from my locations.

Make sure that the *main restricted line also includes the universe and the multiverse as well.
"deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse"

---

