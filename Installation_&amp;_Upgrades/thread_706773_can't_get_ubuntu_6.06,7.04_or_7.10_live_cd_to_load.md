---
title: "can't get ubuntu 6.06,7.04 or 7.10 live cd to load but gos 2.0 beta will? HELP!!!"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by badman35 on 2008-02-24
I built the system that i want to use ubuntu on it is and athon 64  +3200 socket 754 with 512 ram and vid card with 256 ram all msi main board and vid card. So can any of you help been reading up on it but can't figure it out i have 2 other systems with ubuntu on it so i know it may have something to do with hardware. What other info do you need and i will provide??? if i could have gotten ubuntu to run on it would not had to buy xp pro:mad: that is what is on it now infact i am using the systm now to type this so PLEASE HELP!!!!!!!!

---

### Post by Pumalite on 2008-02-24
Did you do md5sum, burn at 4x as image, check for CD integrity before install? If yes; clean your burner lens or try the CD's in different computer. Otherwise it means you'll need the Alternate CD.

---

### Post by badman35 on 2008-02-24
I got the ubuntu cd's from ubuntu . got gos from iso also did alt cd it did not work ether. can put puppy linux cd in and it works to dsl the same they all work but ubuntu and one other cd live cd sabeyon . cd drive is new did cleaning and did cdrom replacement but still nothing ???

---

### Post by badman35 on 2008-02-24
oh almost for got i used those same cd's on all the other systems and they all work.

---

### Post by Pumalite on 2008-02-24
Post how far you get and exact error messages, both, with the Live CD and the Alternate CD.

---

### Post by badman35 on 2008-02-24
i use the 32 bit and the 64 bit edion live cd it will act like it is loading then stop mid way though the main title screen  and caps lock num lock scroll lock all blink at the same time then system reboots. alt cd installs then reboots and stopes.. for error msg can't get one as soon as the keyboard comes back to where it response to key presses it reboots ...

---

### Post by badman35 on 2008-02-24
can use vmware and use live cd's to but not to boot off of and run...

---

### Post by Pumalite on 2008-02-24
After finishing installation with the Alternate CD:
Ctrl+Alt+F1 to get command line
username
password
sudo dpkg-reconfigure xserver-xorg

---

### Post by badman35 on 2008-02-24
> **Pumalite said:**
> After finishing installation with the Alternate CD:
Ctrl+Alt+F1 to get command line
username
password
sudo dpkg-reconfigure xserver-xorg
i have sen that on another thread and did it but was lost and reinstall xp pro to get to use system not in the habit of wiping drives after i get a stable system. but will get another drive and install it and try agan.

---

### Post by Pumalite on 2008-02-24
OK. Good luck.

---

### Post by badman35 on 2008-02-24
i use this system on a daily  as well as my other systems this was the first msi main board i have used and will not use another one. i have a soyo socket A system and every live cd i get will work on it with less memory 256 meg and 256 meg vid also the other one is a fic samba 4518  and it works great to still think it is a hardware problem. but as i typed in previous post will get another drive and reinstall ubuntu alt cd 1 last time..

---

### Post by badman35 on 2008-02-24
> **Pumalite said:**
> OK. Good luck.
thanks for your help so far will post back as soon as i can..

---

### Post by louieb on 2008-02-24
Kind of strange that some Linux live CDs will boot but others won't. I've had that happen to me a few times. It time to play with cheat codes. 
Heres a couple of lists. Just have to look for one that has something to do with the boot problem you are having. 
[BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")
[Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes")

---

### Post by badman35 on 2008-05-13
i have found this post in the documention site [https://help.ubuntu.com/community/Installation/32bitonAMD64]("https://help.ubuntu.com/community/Installation/32bitonAMD64")
if it had not been for this link i would have never been able to install ubuntu on my system " it even workes in livecd mode to"
 i would like to thank everyone at ubuntu and this forum for all your help. I would also like to Specialy Thank the person that made the page the i linked to for the info.

---

