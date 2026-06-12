---
title: "Ubuntu and win7..."
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by Steam. on 2010-02-26
I had Ubuntu and Win7 installed, but recently **i** did something that ****** up the boot manager, so i put the windows 7 cd and repaired the boot manager.BUT, after that, Ubuntu didn't show in boot choices, only Windows 7.I installed it with Wubi, and now when i try to uninstall it, it shows me this:

[IMG]http://www.imagelodge.net/imgs/xlr8/ubuntubqt.jpg[/IMG]

Help?

---

### Post by darkod on 2010-02-26
The wubi entry doesn't exist in your repaired windows bootloader, as you noticed. So it can't find it to remove the entry and it reports the error.
As long as the wubi-ubuntu is deinstalled and removed from Programs, don't worry about this particular message. But I'm not sure if this error is stopping the deinstall process. Not using wubi myself.

---

### Post by Steam. on 2010-02-26
That error is stopping me from uninstalling ubuntu.

---

### Post by whitedemon on 2010-02-26
Why don't u take a complete back up of wat u want and format the primary partition and windows sys partition while using the 7 installation CD, do format the linux partition. 

First install 7 and then use the install as a windows application for Ubuntu? 

I had the same probs like urs. But then i got it solved now. 

Ubuntu Forums Rocks
White Demon

---

### Post by Steam. on 2010-03-02
But any way without formatting?I know how to do it, but i have loads of stuff on that HDD that would take ages to copy to another one.

---

### Post by darkod on 2010-03-02
Have you confirmed it's actually not uninstalled? Does it still exist in Programs and the folder ubuntu in the partition where you installed?

---

### Post by Mark Phelps on 2010-03-03
Since you did a Wubi install, if you installed Wubi to a different partition than the Win7 OS, the Wubi "file" is still there.  The entry got wiped from the BCD because that was completely rewritten when you did the Win7 reinstall.

Have you tried reinstalling Wubi and pointing to the same other partition?

---

### Post by Steam. on 2010-03-05
I tried uninstalling it and it can't continue from that error.And i cant reinstall it if i dont uninstall this one first(which as you can see, is impossible)

And Ubuntu is shown in programs, i tried to uninstall it from there but still no luck.

---

### Post by Steam. on 2010-03-08
Bump.

---

### Post by Mark Phelps on 2010-03-08
Try the stuff in the Uninstallation section of the linked Wubi Guide:

[https://wiki.ubuntu.com/WubiGuide#Uninstallation]("https://wiki.ubuntu.com/WubiGuide#Uninstallation")

---

### Post by Steam. on 2010-03-10
> **Mark Phelps said:**
> Try the stuff in the Uninstallation section of the linked Wubi Guide:

[https://wiki.ubuntu.com/WubiGuide#Uninstallation]("https://wiki.ubuntu.com/WubiGuide#Uninstallation")

Thank you.The manual uninstallation section helped me :)

---

### Post by Mark Phelps on 2010-03-10
Glad to be of help ...

---

