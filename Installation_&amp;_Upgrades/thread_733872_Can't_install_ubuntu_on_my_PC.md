---
title: "Can't install ubuntu on my PC"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by olaB on 2008-03-24
Hi.

I get this error when I try to install Ubuntu on my PC:

[IMG]http://skjomen.net/error/error.gif[/IMG] 

Her is what's in my PC.
[http://skjomen.net/error/MyPC.htm]("http://skjomen.net/error/MyPC.htm")

Hope someone can help mi.

---

### Post by Pumalite on 2008-03-24
Install with the Alternate CD

---

### Post by housam on 2008-03-24
Try to format one of your HDD and create instead of it two partitions - one as a root ( / ) ext3 format and the other as a swap ( 2 GB is ok ). and during the installation assign them manually

---

### Post by olaB on 2008-03-24
Hi and tank you for quick response.

I try the alternate installation. But when I com to the partitioning tool it wasn't able to see the disks.

olaB

---

### Post by Pumalite on 2008-03-24
Are you using Windows now?

---

### Post by olaB on 2008-03-25
Yes, Windows Vista Home Premium

---

### Post by uberlube on 2008-03-25
I had the same problem when i first started using Linux (not being able to see the disks) Although it was the LiveCD that wouldnt show them, and the alternate install disk worked perfect. Grab yourself PartedMagic and burn it to disk, then boot it like a liveCD and create your Linux partitions using visparted. Then retry the alternate install disk.

---

### Post by olaB on 2008-03-25
> **uberlube said:**
> I had the same problem when i first started using Linux (not being able to see the disks) Although it was the LiveCD that wouldnt show them, and the alternate install disk worked perfect. Grab yourself PartedMagic and burn it to disk, then boot it like a liveCD and create your Linux partitions using visparted. Then retry the alternate install disk.

Try'd this. Still not able to see the disks

---

### Post by olaB on 2008-03-26
anyone who can helpe me?

---

### Post by housam on 2008-03-26
Boot from the live CD and send a screen shot of your partitions using Gparted tool .

---

### Post by olaB on 2008-03-26
This is wot I se when I try to install from the live-CD
[IMG]http://skjomen.net/error/Screenshot-Install%C3%A9r.png[/IMG]

---

### Post by Pumalite on 2008-03-26
Get Gparte3d Live CD and try with that: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Post screenshot

---

### Post by housam on 2008-03-26
boot from the live CD , then go for system >> admins. >> partition editor . which will show the actual partitions of your Hard disks.

---

### Post by Tomatz on 2008-03-26
> **olaB said:**
> Hi and tank you for quick response.

I try the alternate installation. But when I com to the partitioning tool it wasn't able to see the disks.

olaB

Maby your bios isn't set up correctly?

Have a fiddle with your drive priorities. It could even be a jumper on your hdd not set to master.

---

### Post by olaB on 2008-03-26
> **Pumalite said:**
> Get Gparte3d Live CD and try with that: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Post screenshot

[IMG]http://skjomen.net/error/gparted.jpeg[/IMG]

---

### Post by damispyderbyte on 2008-03-26
Hey had that same problem. All you have to do is type irqpoll as a special command when you install. Noapic command might also help

Tyler

---

### Post by Pumalite on 2008-03-26
If you are using XP, right click on it and choose 'resize from the menu. Make the new partition 'extended'. In this new space, make 3 'New' partitions:
!0 GB for '/'
1 GB for /swap
The rest for /home.
Install Ubuntu, go 'Manual and use the partitions already prepared.

---

### Post by olaB on 2008-03-27
Thank you all for the help. What  ever I do, I can't find the disks. And at last the PC did crash.

---

