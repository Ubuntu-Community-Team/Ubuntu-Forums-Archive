---
title: "Running into a problem installing 10.04"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by DmitryGub on 2010-07-25
This is what I did:
1. Created 20GB partition
2. Formatted it as F: and FAT32
3. Inserted the CD
4. Picked "Install inside Windows"
5. Picked the drive that I just partitioned ( F: )
6. Let the installation run
7. Picked "Reboot Now" once the CD ejected

So here are my problems:
a) When I restarted, I was not given any options to boot to Ubuntu
b) When I got back into Windows automatically, it didn't continue installing anything
c) Now I can't uninstall Ubuntu from that partition because it gives me an error
d) I wanted to try again, but now I can't format/delete the partition with Ubuntu on it

Can someone tell me what's going on? I did this exact same process on my desktop, and everything went smoothly.

I mean, even if someone helped me with c) or d), it'd be great, because right now I have 20GB I can't use on my HDD.

Oh yeah, I'm using Windows 7 right now.

---

### Post by partloer on 2010-07-25
Hi DmitryGub,

I have a few ideas to help you out.  A few points I wouldn't create a partition first with FAT32.  Linux uses a different format so when you install Ubuntu I wouldn't manually setup the partition.  I would just load the CD then with the install you can choose the size of the Ubuntu partition depending on the amount of free space [seen here in step 6]("https://help.ubuntu.com/community/GraphicalInstall").  

As for your current problem it seems that the boot loader didn't get install correctly so what I would do is once you boot up in Windows remove the Ubuntu partition then try the graphical install where you dual boot Ubuntu and Windows.  

There are a lot of forum topics on this subject not to mention on the web.  I would read up on this process on the web a little more so that you understand this then give it a try.

Also you can ask more questions if you don't know.

---

### Post by DmitryGub on 2010-07-26
Okay cool, it works now, thanks! I still don't understand why it didn't work the previous way... I did the exact same process on my desktop. Oh well.. :D

---

### Post by VH-BIL on 2010-07-26
I am pretty sure there is an option to use free space when installing ubuntu. So if you delete the fat32 partition it will use that space. This is just from memory I could be wrong.

---

