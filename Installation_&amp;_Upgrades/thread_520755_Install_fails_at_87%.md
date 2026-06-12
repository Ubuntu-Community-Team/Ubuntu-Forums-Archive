---
title: "Install fails at 87%"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by nroussi on 2007-08-08
Hi all,
I am trying to install edubuntu 7.04 and it fails at 87%. System specs:
3ware raid 3650SE raid level 5 (latest fw version)
tyan s2925 (later fw version)
4x samsung 500GB
8GB 3200 ram
When I try to install to the hard disk, I go through all the steps but when it tries to install a specific packed at arounf 87% the machine just shuts down.
After a few tries, I downloaded the live CD and I booted to live CD. After it booted up, I did
apt-get install edubuntu-server
It downloaded all the packages but when it started installing, the computer just shut down again. Does anyone know what is going on?
Appreciate any suggestions....

---

### Post by PryGuy on 2007-08-08
There's some bug with server install I guess. I tried to install Ubuntu server from the DVD, I chose 'Install Ubuntu Server' from the boot menu, it booted in alternative (text) install mode, started the install process and just froze at 85 percent during the file copying process. I tried to reinstall many times, result was the same, the system froze at 85 percent... It froze not hung 'cause I could switch to another consoles.

---

### Post by thezoed on 2007-09-03
Mine froze at 85% for about 40 minutes, then started spinning the cd again.  I was just about ready to try the suggestion of ejecting the cd and reinserting it when it did this.

---

### Post by PryGuy on 2007-09-03
> **thezoed said:**
> Mine froze at 85% for about 40 minutes, then started spinning the cd again.  I was just about ready to try the suggestion of ejecting the cd and reinserting it when it did this.So your installation was successful?

---

### Post by muguwmp67 on 2007-09-30
I'm having this problem too.  I'm installing Feisty on a machine with no internet connection.  Is this the cause of the problem?  This has happened to me installing from an Ubuntu CD and DVD

Is an internet connection required for a Feisty install?

---

### Post by PryGuy on 2007-09-30
Yes, mates, I think I solved the problem! The thing occurs when the text installer tries to fetch package information from the internet. You'll see it if you press Alt+F4 when it pauses. The solution that worked in my case, I chose "do not configure at this time" for my network interface.  You can unplug the network cable before the network interface configuration also if you have DHCP and you do not see this menu. It worked for me.

---

