---
title: "Update without using apt-get"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by woody22075 on 2007-10-01
I an a linux noobie.  I just installed 7.04 on my laptop as a dual-boot with vista.  I need to update but dont have a functioning internet connection through Feisty yet (so no apt-get, etc.).  I do, however, have internet access with vista (through wireless).  

I want to update but how can i do this without apt-get?  Is there a way i can access the updates through vista and then install them when i relogin in ubuntu?

thanks for the help!!!

---

### Post by maybeway36 on 2007-10-01
I wouldn't nessecarily say you need to update. Even securtiy updates won't be important until you connect to the Internet with Ubuntu.

---

### Post by woody22075 on 2007-10-02
Im afraid I do need to update (also get missing dependencies).  Any advice?

---

### Post by picopir8 on 2007-10-02
What kind of wifi card do you have?  

In many cases, the drivers were loaded but they may be restricted.  In that case, go to system-administration-restricted drivers manager and enable the driver.

If you do not have the drivers loaded at all, then you need another means of getting the drivers from the internet.

In that case you could:
1) Connect using the wired ethernet port on your computer (assuming you have one) and either plug it in to a wired ethernet jack with internet access or plug it into a wireless bridge and then connect to your wireless network.

2) Download the drivers from another computer or while booted to windows, then put them on CD, external HD, thrumbdrive, etc. and then install them using dpkg.

---

