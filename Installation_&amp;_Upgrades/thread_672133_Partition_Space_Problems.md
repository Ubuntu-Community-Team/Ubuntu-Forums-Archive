---
title: "Partition Space Problems"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by ellusionist on 2008-01-19
I want to install Ubuntu 7.10, however, when it comes to the partition step it forces me to partition no less than 90GB(60%). I don even have this amount of free space left. I only want to partition 15gb. How can I achieve this?

---

### Post by Pumalite on 2008-01-19
XP or Vista?

---

### Post by chewearn on 2008-01-19
You can prepare the empty space when you wish to install on, **before** you start the installer.   Use the Partition Editor that comes with the livecd, or any other (your choice).  Then you don't have to grapple with the un-user friendly (my opinion) partition editor in the installer.

Else you can install first, then use the livecd partition editor to resize later.

---

### Post by Pumalite on 2008-01-19
With Vista, you have to allocate space for Ubuntu from WITHIN Vista, with the Vista partitioner; otherwise Vista will not let you run anything in that computer.

---

### Post by ellusionist on 2008-01-19
I am using XP. I tried using the tool that comes with the live cd but that also forces me to partition no less than 90GB. 

Are there any free easy to use Partition Tools?

---

### Post by Pumalite on 2008-01-19
Use Gparted Live CD (the stand alone program):
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk, boot from it and resize your XP partition to your hearts desire.
Don't forget to backup first.

---

### Post by ellusionist on 2008-01-19
Thanks. Just to confirm before I start, in the "free space preceding" box do I put the amount of space(15GB) that I want for my Ubuntu partition?

---

### Post by Pumalite on 2008-01-19
When you resize, you MUST specify the size of the new partition. (aprox 18000 is what you want)
You want to shrink XP to the left.

---

### Post by ellusionist on 2008-01-20
Thanks for the responses, but after trying to use the Ubuntu partitioning that comes with the install it bombed out with an error and screwed up my Windows XP! Can hardly run anything. Gonna have to do a clean install of Windows and gonna rather stick to it full time.

---

### Post by Pumalite on 2008-01-20
I tol you to use the Gparted Stand Alone Program.

---

### Post by ellusionist on 2008-01-20
> **Pumalite said:**
> I tol you to use the Gparted Stand Alone Program.

I did. It doesnt even allow me to partition. Just stays on the same hard drive size and unable to move anything.

---

### Post by magump on 2008-01-20
Have you tried WUBI, which will run Ubuntu inside windows?  The link for the download is: [http://wubi-installer.org/](http://wubi-installer.org/)  There is no partitioning, etc.

---

### Post by Pumalite on 2008-01-20
> **ellusionist said:**
> I did. It doesnt even allow me to partition. Just stays on the same hard drive size and unable to move anything.
Read the Manual.

---

