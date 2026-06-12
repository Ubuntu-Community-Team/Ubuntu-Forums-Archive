---
title: "Virtual Box - Virtual Machine"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by nrd80v on 2010-08-08
Dear All
I have some questions on V-Box and the Virtual Machine.

1) Can we change the display size of Virtual Machine; even in full screen mode it is too small for me (I use Ubuntu as the Host and Windows XP as Guest)

2) Can I increase the Hard Disk space of Virtual Machine. I gave it 5GB instead of 15GB. I added a hard disk image as a slave; etc., but it never worked

3) Can I share Virtual Machine with the Host Machine - I want Host to access Guest Files and Vice Versa

Please help me in the above
Yours
V. Narayanan
[email]nrd80v@yahoo.com[/email]

---

### Post by drdos2006 on 2010-08-08
All of your answers are in the Help section of Virtualbox. Run Virtualbox and click on Help. 

regards
PS. All the answers you queried are in the Help section.

---

### Post by Ginsu543 on 2010-08-09
> **nrd80v said:**
> 
1) Can we change the display size of Virtual Machine; even in full screen mode it is too small for me (I use Ubuntu as the Host and Windows XP as Guest)

Yes, you can use the Display applet in Control Panel inside your Windows guest to resize the display.

> **nrd80v said:**
> 
2) Can I increase the Hard Disk space of Virtual Machine. I gave it 5GB instead of 15GB. I added a hard disk image as a slave; etc., but it never worked

This depends on whether you set up your virtual disk image in dynamic (changes upon your needs) or static mode (stays the same no matter what). Dynamic mode is more versatile (you don't have to worry about running out of space) but Static mode is faster. If you set up you 5 GB .vdi as static, then there is no way to increase its size. What you can do is create another larger .vdi file (say 15 GB) and use a partition imaging software to copy your VM into the larger one.

> **nrd80v said:**
> 
3) Can I share Virtual Machine with the Host Machine - I want Host to access Guest Files and Vice Versa

You can do this by setting up shared folders which will show up both in Ubuntu and in your Windows guest.

---

