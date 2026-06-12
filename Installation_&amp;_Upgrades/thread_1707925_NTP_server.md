---
title: "NTP server"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by govenkat on 2011-03-16
hi,
   
  I installed UEC in my server.i want to make my server as ntp server but i am not having internet access.so can you please help me how to install ntp server without internet.
   
  help me please..........

---

### Post by kagerato on 2011-03-16
This is such a strange request I'm beside myself.  Might I ask what use the NTP server is going to be on a machine that is...not connected to the network ?

The most common NTP package is literally just called 'ntp'.  It's typically installed by default, if I remember correctly.  You can also install it off an Ubuntu Live CD or DVD.  `sudo apt-get install ntp` , or use your favorite package manager.  (You may need to add the CD in the repositories options, or manually edit **/etc/apt/sources.list** .)

---

