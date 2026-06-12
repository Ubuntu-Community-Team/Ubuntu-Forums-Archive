---
title: "JDK 6 Update 4 with NetBeans 6.0 installation fails"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by sadasith on 2008-02-01
Hi,

I have downloaded the above titled bundle from java.sun.com. When i run the .sh file it runs until showing a window where no content is visible. When i run the file through the terminal it reports the following issues and stops at that point.

/usr/share/themes/Human/gtk-2.0/gtkrc:71: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:242: Priority specification is unsupported, ignoring

I'm on the newest Ubuntu Gutsy Gibbon. Can anybody give a solution to proceed with the installation?? OR will i have to install jdk6 using Synaptic Package Manager??

I show several posts pointing out this bug. But didn't see any proper reply to overcome the issue. Hoping for a solution to the point. :)

---

### Post by Partyboi2 on 2008-02-02
what happens if you changed theme's from human to something else?

---

### Post by hofa on 2008-02-02
I found this in another thread:

System > Preferences > Appearance > Visual Effects
Here you've got to select 'None' and after the install you can switch it back.

---

### Post by ahpatsuma on 2008-02-02
I've installed JDK 6 Update 4 on ubuntu gusty when i test java i've no image when i do : 
sudo updatedb && sudo ln -fs `locate libjavaplugin_oji.so | grep /ns7/libjavaplugin_oji.so` /usr/lib/mozilla/plugins
i get the message: updatedb: fatal error: load_file: Could not open file: /etc/updatedb.conf: No such file or directory
and there's no file named  updatedb.conf in /etc
please help

---

### Post by sadasith on 2008-02-02
ahaa...thanks hofa. It worked really fine!!! :)

---

