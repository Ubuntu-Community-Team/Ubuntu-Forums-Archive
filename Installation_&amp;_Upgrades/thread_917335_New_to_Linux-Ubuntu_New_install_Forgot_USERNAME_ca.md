---
title: "New to Linux-Ubuntu New install Forgot USERNAME can't login"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by pctechwantab on 2008-09-11
New to Linux-Ubuntu New install Forgot USERNAME can't login after the first boot Please help

---

### Post by phidia on 2008-09-11
You can boot in rescue mode (press the tab or esc key at the grub menu if you don't see the grub menu) and then open a terminal and enter "users" that will show your user name.

---

### Post by benjick on 2008-09-11
> **phidia said:**
> You can boot in rescue mode (press the tab or esc key at the grub menu if you don't see the grub menu) and then open a terminal and enter "users" that will show your user name.

users is only for logged in users?

type cat /etc/passwd and your username should be at the bottom

---

### Post by y@w on 2008-09-11
> **benjick said:**
> users is only for logged in users?

type cat /etc/passwd and your username should be at the bottom

Or you can do an ls of /home. Most likely the username will be the name of the home directory.

---

### Post by pctechwantab on 2008-09-12
How does one do a rescue boot or any of the other possible solutions. I'm very "green" to Linux. I do want to learn so I can dump M$. I do have Win XP on my Laptop/Notebook also. XP is the primary partition and I installed Ubuntu onto the HD after.

Richard

---

### Post by robert shearer on 2008-09-12
> **pctechwantab said:**
> How does one do a rescue boot or any of the other possible solutions. I'm very "green" to Linux. I do want to learn so I can dump M$. I do have Win XP on my Laptop/Notebook also. XP is the primary partition and I installed Ubuntu onto the HD after.

Richard

see post #2 above.
When you first start your computer you should see a screen that lists your Ubuntu installation and your xp/Windows installation as options to boot. 
Use the up/down arrows to find Ubuntu Recovery mode,select it and press enter.
It will boot to Ubuntu rescue mode terminal where you can run the commands given by the other posters.


Just a question though,  did you do a full Ubuntu install or did you install Ubuntu under Windows using Wubi???

Oh, and have you forgotten just your username or both username and password??

---

### Post by tuxerman on 2008-09-12
A 'rescue boot' is possible with the help of the "recovery" option in the GRUB boot menu. It logs you into a full-control root user mode. Be careful, though :)

As always, the LiveCD is the best rescue option. This is especially when you want to deal with partitions, and want to do something to your current linux partition.

---

### Post by pctechwantab on 2008-09-12
> **robert shearer said:**
> see post #2 above.
When you first start your computer you should see a screen that lists your Ubuntu installation and your xp/Windows installation as options to boot. 
Use the up/down arrows to find Ubuntu Rescue mode,select it and press enter.
It will boot to Ubuntu rescue mode terminal where you can run the commands given by the other posters.


Just a question though,  did you do a full Ubuntu install or did you install Ubuntu under Windows using Wubi???

Oh, and have you forgotten just your username or both username and password??
Ok I think the install was the latter but not sure, I would have to Iook at Firefox's history to goto those pages to see what I chose. I think I remember the username I do know the password. I did notice on the login screen in the bottom Right corner it said my name (Richardhulett) computer would that possibly be the username? 

Richard

---

### Post by pctechwantab on 2008-09-12
I forgot to mention that I'll try that when I'm done running Kaspersky WebScanner. I picked up a bug again. 

Richard

---

### Post by pctechwantab on 2008-09-12
Ok I'm in it was as I thought my name in the lower right corner.  Ok now the next question. I noticed after the system was up there was 119 updates. 

Are there Anti virus/malware/adaware programs that are needed for Linux systems.? Where or what is a good source to learn Linux?

Like I said I want to learn Linux well enough so I can Ditch M$.

Thank you to all who have helped

Richard

---

### Post by robert shearer on 2008-09-13
ok, great to hear it is all working. 
Yes, there will be a number of updates. click on the update icon and the update manager will open.
Make sure that you are connected ie modem plugged in and ready.  Then click on Install updates and wait while they are downloaded and applied (lots to download so hopefully you are on broadband?)

here is the beginner link..
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

No you don't need the ad-aware etc etc relax,this is Linux and we don"t need to worry about windows malware. Read the beginner link above then use the forum search function to find out more about virus/malware etc untill you are happy.

---

### Post by IndyGunFreak on 2008-09-13
[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

Another interesting Link about Anti-virus and Linux.

---

