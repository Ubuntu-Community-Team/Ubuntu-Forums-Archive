---
title: "Restore backup"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by wildmanne39 on 2011-12-07
Hi, my computer has crashed and I have back ups of my home folder and a few others, my question is I have over 20 operating systems installed in virtualbox that I use for testing and writing guides the files are in my home folder and they get backed up nightly can I just restore them and they will work or do I need to export each one to my external drive and then import them after I have reinstalled like I did the last time?

Thank you in advance all help is appreciated.

---

### Post by Old_Grey_Wolf on 2011-12-07
The virtual disk images will be in your /home. If you need to reinstall Virtualbox you will need to tell Virtualbox to use and existing virtual disk image as you create the VMs for each OS. Browse to the /home/[user]/VirtualBox VMs folder and select the OVF, vdi or vmdk file for each OS. If you have the /home/[user].VirtualBox backed up, you may not need to recreate the VMs. I have had to edit the /home/[user].VirtualBox/VirtualBox.xml file to sort out some problems.

---

### Post by wildmanne39 on 2011-12-07
Hi, thank you for that information, I will give it a shot.

---

