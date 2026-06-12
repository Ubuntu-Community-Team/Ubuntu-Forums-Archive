---
title: "Failed instillation – Black screen on start up"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by kippa on 2008-05-15
Hi all

I am a fist time user of Ubuntu, made the switch from vista- as it was starting to irk me. I burnt a live CD with ubuntu 8.04, everything worked great as I was able to run it off the CD. As I decided to install it making it my premier operating system I ran into a bit of trouble during the partitioning part of instillation. It came up with an error (cant remember it off the top of my head). So I canceled the install process. 

I decided to reboot, but found that nothing will come up. All I see after the initial load screen is a black screen with a grey flashing bar. It remains like this. 

What I either need to achieve is get back into vista (doubtful) or reboot off the CD using Ubuntu (if that’s possible?) I have tried to re-boot from the DVD drive by pressing F2 and selecting it, but this does not seem to work.

I Have an Acer Aspire 5920

Any help would be greatly appreciated.

---

### Post by Pumalite on 2008-05-15
Fix your Windows MBR with Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it.
Boot your Ubuntu Live CD and post:
sudo fdisk -l

---

### Post by az on 2008-05-15
> **kippa said:**
> Hi all

I am a fist time user of Ubuntu, made the switch from vista- as it was starting to irk me. I burnt a live CD with ubuntu 8.04, everything worked great as I was able to run it off the CD. As I decided to install it making it my premier operating system I ran into a bit of trouble during the partitioning part of instillation. It came up with an error (cant remember it off the top of my head). So I canceled the install process. 

I decided to reboot, but found that nothing will come up. All I see after the initial load screen is a black screen with a grey flashing bar. It remains like this. 

What I either need to achieve is get back into vista (doubtful) or reboot off the CD using Ubuntu (if that’s possible?) I have tried to re-boot from the DVD drive by pressing F2 and selecting it, but this does not seem to work.

I Have an Acer Aspire 5920

Any help would be greatly appreciated.

If you were once able to boot into the live cd, but now you cannot, it seems like a hardware problem.

---

### Post by kippa on 2008-05-15
> **Pumalite said:**
> Fix your Windows MBR with Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it.
Boot your Ubuntu Live CD and post:
sudo fdisk -l

So far so good. Thank you so much!

---

### Post by Pumalite on 2008-05-15
Did you use Super grub?
Post the output I ask you for.

---

