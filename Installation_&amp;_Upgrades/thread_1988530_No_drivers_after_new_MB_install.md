---
title: "No drivers after new MB install"
date: 2012-05-27
forum: Installation &amp; Upgrades
---

### Post by oohbuntoo on 2012-05-27
I installed 10.04 LTS 64bit flawlessly with a Biostar TA890FXE MoBo.  This OS is on it's own hard drive.  I recently installed a Gigabyte GA-990FXA-UD3 MoBo.  I am unable to download any drivers because I can't get on the net.  No net = no drivers.  I'm hoping it is possible to get up and running without having to re-install Ubuntu because 'cuz I have it set perfectly.  What are my options here?  Thanks in advance :P

---

### Post by oldfred on 2012-05-28
Vendors normally do not provide any drivers for Linux ony Windows. 

Can you not boot?

---

### Post by mastablasta on 2012-05-29
try and boot from latest liveCD. in linux drivers are a part of kernel and 10.04 kernel is 2 years old. so you might need either 12.04 or somehow get the new kernel on your old 10.04 install.

---

### Post by oohbuntoo on 2012-05-30
Yes, I can boot.  I can do everything except what requires an internet connection.

---

### Post by oohbuntoo on 2012-05-30
> **mastablasta said:**
> try and boot from latest liveCD. in linux drivers are a part of kernel and 10.04 kernel is 2 years old. so you might need either 12.04 or somehow get the new kernel on your old 10.04 install.
What I find strange is I first installed Ubuntu [forgot the version] on an ECS 6100-something GeForce MoBo.  When I replaced that MoBo with the Biostar TA890FXE, all I had to do was reload the Nvidia drivers for the PNY 550 Ti GPU to get my display correct.  It went swimmingly after that.  So, I thought it would work the same with installing the Gigabyte GA-990FXA-UD3 MoBo.  I was obviously wrong.

---

### Post by oldfred on 2012-05-30
You probably just have to reset the Internet configuration. It may be the wrong version and just stopping that and starting the new would solve it.

But you need to as that question specifically. I have seen several similar threads on Internet connection issues. Search forum and if you do not find a solution start a new thread wtih the MB and Internet configuration in the title.

---

