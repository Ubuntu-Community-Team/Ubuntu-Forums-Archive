---
title: "Windows disables ubuntu startup"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by shervin2 on 2014-05-13
Hi,
I had only installed Ubuntu 12.04 LTS on my laptop and in a few months I realized I needed windows as well. so I tried to install windows 8.
when trying to install it I ran into a problem, I had no free disk! so I backed up my /home partition and I converted it to free space and I created a new partition for windows.
and after that I couldn't boot Ubuntu + I didn't have a /home partition. please help me!!
what can I do??

---

### Post by T.J. on 2014-05-15
Probably the sanest course when dealing with Windows 8, especially if you have very little experience with bootloaders is to install Windows 8 first and then install the Linux of your choice afterward.  Windows has a tendency to want to take over the bootsector if it is installed after Linux, because Windows doesn't care if another bootloader is present.  

There is a way to reinstall the existing bootloader, but I'd need to know more about your laptop first: if it is using standard BIOS or a new style called UEFI. If you don't know that's okay but it will take some questions.

---

