---
title: "Install crashes about half-way through"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by jcaplis on 2011-01-03
So I've been trying to install on an older PC so my sister can use it for light web browsing. The first time I installed it gave me an error about half-way through, something about not being able to read the disk and possible fixes were to burn a new cd, try a new cd drive, and trying a new HDD. Well, I've tried multiple copies of Ubuntu and multiple versions, several HDDs and several optical drives. Each time I've gotten to the same point and then the installer crashes. I'd like to note that I am able to run Ubuntu off of the disk without installing.

Any thoughts as to what might be causing this? I'm at my wits end. I will try to supply any additional data if I can, just let me know what you need.

---

### Post by Lessss on 2011-01-09
I tried an install and the graphic went wonky right away. Then I tried booting from CD and again graphics went wonky. The disc passed integrity check. 

I installed 9.1 no prob then upgraded and again graphics went wonky.

I'll try downloading and burning another iso later in a few months.

---

### Post by Evandar on 2011-01-09
> **jcaplis said:**
> So I've been trying to install on an older PC so my sister can use it for light web browsing. The first time I installed it gave me an error about half-way through, something about not being able to read the disk and possible fixes were to burn a new cd, try a new cd drive, and trying a new HDD. Well, I've tried multiple copies of Ubuntu and multiple versions, several HDDs and several optical drives. Each time I've gotten to the same point and then the installer crashes. I'd like to note that I am able to run Ubuntu off of the disk without installing.

Any thoughts as to what might be causing this? I'm at my wits end. I will try to supply any additional data if I can, just let me know what you need.

I am trying to do the exact same thing and I had similar problems. I'll tell you what I did and I hope it works for you too. This will be far, far easier if you are already working on an Ubuntu machine.

1st. Grab an external hard drive and backup everything inside it on your current computer. This will prevent having to burn multiple CDs.

2nd. Format the drive using a FAT system.

3rd. Download the **alternate disc** iso. Since this is an old machine, I'm assuming right away that you have less than 256 MB of RAM, which will give you tons of problems when installing normally. Using this is foolproof.

4th. Use the startup disc creator of Ubuntu to make your external drive bootable with the alternate disc iso. 

5th. Boot from the drive on the old machine. You can do a normal install if you want, but a command line install is preferable when on an old machine. If you have the command line, you can work your way up and install a GUI.

Hopefully, without any errors, next time you boot you will be in the command line.

By the way, Ubuntu will be very slow on an old machine. You're far better off downloading a lightweight WM/GUI. Make sure you've read this thoroughly.

[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

