---
title: "Ubuntu 7.10 Server installation freezes"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by pheadm on 2008-02-05
This is my first time to use Ubuntu (Linux for that matter). I had no difficulty installing the desktop version of Ubuntu 7.10. But we needed the Server version so I downloaded the iso and burned a CD of it. When I tried installing the Ubuntu 7.10 Server on top of the Desktop version, things are doing well until it freezes when the base system installation is 85% complete (the screen shows "Installed cupsys-bsd"). I tried re-installing again and it freezes again on that part. Can anyone help me?

The computer I'm using is HP Proliant ML 110 G4 with 2GB memory. The root directory is partitioned with 70GB of space. Thank you for your help.

---

### Post by Partyboi2 on 2008-02-05
did you check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") when you downloaded the server version?

---

### Post by jeepGuy on 2008-02-05
We had a similar experience with Ubuntu Server 7.10 on a Dell at about the same place. As  it turns out, what looked like a freeze was a very, very long pause. Re-run your install and let the system sit, then report back.

---

### Post by Odrodzona-Sarmacja on 2008-02-05
Yeah, I noticed that once myself. Solution is to disable internet connection during installation. It kills the venom of the slow and dangerous Ubuntu updater, which is run during installation too. :D

BTW. From january also there is a dangerous Ubuntu's security update that will screw the synaptic manager in Ubuntu 7.10, so it won't install or remove anything no matter what. :( Which one it is, I still have no idea. Installing Ubuntu's security updates became lately just too dangerous, unless someone is for fun of reinstalling Ubuntu every 3 days until Ubuntu 8.04 will be released. :D

---

### Post by pheadm on 2008-02-05
> **Partyboi2 said:**
> did you check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") when you downloaded the server version?

Partyboi2, yup I checked the md5sum and even had the CD checked before the actual installation. Am reinstalling again and will follow jeepguy's advice to wait. Will update you soon.

---

### Post by pheadm on 2008-02-06
It's now 5 hours since I started re-installing Ubuntu Server 7.10 and again it hangs on the 85% installation of the base system. I also disconnected the internet cable as suggested but to no avail. Any other ideas guys?

---

### Post by XanderTM on 2008-04-17
Well, CUPS is the Printer configuration, so try turning your printer on, if you have one. It worked for me.

---

