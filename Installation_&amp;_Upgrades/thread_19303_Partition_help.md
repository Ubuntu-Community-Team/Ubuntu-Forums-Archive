---
title: "Partition help"
date: 2005-03-11
forum: Installation &amp; Upgrades
---

### Post by sethosayher on 2005-03-11
I currently have a windows OS, with about 9 gigs of free space (I wish to use 5 for Ubuntu)... I'm horrible when dealing with partitions. What kind of partitons should I make, and how many of them? I also have partition magic, so if anyone has experiance with that program, can someone also tell me what to do with it? 

Thanks in Advance.

---

### Post by sethosayher on 2005-03-11
Can anyone help me? I just want to know what types of partitions I should make (I want to give up about 5 gigs)

---

### Post by sethosayher on 2005-03-11
Oh, I also want to apologize if this question has been asked before, I searched for previous threads and didn't find any topics that answered my question. I'm not really a newbie to linux, I have used Debian for a while, but never dual booted with windows on the same drive...

---

### Post by jrasmussen0 on 2005-03-11
You just need to limit the Windows partition to the 9 gig and have the 5 gig unused.  Ubuntu will do the rest of the partitions during the install.  Use Partition Magic for this.

---

### Post by sethosayher on 2005-03-11
So, I'll just resize the Windows Parition? I'll try it, thanks.

---

### Post by sethosayher on 2005-03-11
I have installed Ubuntu, but I cannot access the internet from within ubuntu. When I used the Live CD, I was able to go online without a hitch. I recall that, when installing, one error I had was that the DHCP wasn't configured right, and not knowing how to fix it, I let it be. I don't understand what is going on...I also think that Ubuntu connected to some servers during the installation and downloaded some more packages. Does anyone know how to fix this?

---

### Post by Xian on 2005-03-11
[QUOTE=sethosayher]I recall that, when installing, one error I had was that the DHCP wasn't configured right, and not knowing how to fix it, I let it be. [/QUOTE]
This happened to me on a couple of installs, but instead of actually finishing out the process, I just repeated the DHCP configuration step using the installer and it always managed to get it properly setup on the next attempt.

---

### Post by bored2k on 2005-03-11
Upper Panel > System Configuration > Networking

This will allow you to set up your DHCP/Manual config/Proxy. When asked for password, its your user password. [ubuntu uses sudo instead of su]

---

### Post by sethosayher on 2005-03-12
[QUOTE=bored2k]Upper Panel > System Configuration > Networking

This will allow you to set up your DHCP/Manual config/Proxy. When asked for password, its your user password. [ubuntu uses sudo instead of su][/QUOTE]

Thanks, I'll try it.

---

