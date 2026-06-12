---
title: "only booting to grub"
date: 2015-03-12
forum: Installation &amp; Upgrades
---

### Post by mrsteve0924 on 2015-03-12
first time installing and using linux. did a lot of reading  to make sure i installed correctly since i am currently dual booting  with windows 7 and 8. windows 7 on an ssd and windows 8 on an HDD. i  decided to install Ubuntu on the HDD on a second partition. 
  I installed the boot loader in the same partition as ubuntu and then  used easybcd to add  grub to the Windows boot menu.  Rebooted, selected  Ubuntu to from boot menu, but it booted into a command line interface  instead of GUI. 


  Most fixes I read are to enter some commands that I am not  comfortable with being brand new to linux.  I also read that i might  have to install the nvidia drivers, but not sure how from a command  line. 


  had no problems when i just tried Ubuntu from live cd. 


  thanks for the help

---

### Post by yancek on 2015-03-12
When you select Ubuntu from the EasyBCD menu, do you see the Ubuntu Grub boot menu with various options?  If you don't, the problem is with EasyBCD.  Try it again.  If you do post back as there are ways to do a one time edit from the Grub boot menu so that you can boot to a GUI.

---

### Post by mrsteve0924 on 2015-03-12
i see no various options for grub2 in easybcd

---

### Post by mrsteve0924 on 2015-03-12
> **yancek said:**
> When you select Ubuntu from the EasyBCD menu, do you see the Ubuntu Grub boot menu with various options?  If you don't, the problem is with EasyBCD.  Try it again.  If you do post back as there are ways to do a one time edit from the Grub boot menu so that you can boot to a GUI.

so based on what you said about easybcd i realized i didnt have the latest version.  re-installed it, added grub and got to my desktop!

thanks for the help.

---

