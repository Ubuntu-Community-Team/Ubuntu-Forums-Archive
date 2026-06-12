---
title: "how can i ...."
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by freefixkorma on 2010-01-15
hi guys i am sorry if this is not the correct subject to post i have ubuntu 9.04 i want to know if i can do a partition base on what i have right now cause when i installed ubuntu i didnt do the partition to install windows so i want to do it now or in any case how can i reinstall ubuntu again without loosing my data store in my hard drive will appreciate any advise concerning this issue please post any help what is best to be perform in my pc i am very happy with ubuntu and wanna keep with it but sometimes a have some app in windows that i need thanks in advance

---

### Post by Cabs21 on 2010-01-15
get gParted and use it to partition out a section to install windows to.

```
sudo apt-get install gparted
```or go to the add software tab under applications and search for gParted.

it is light and perfect for what you need to do.

You will not need to reinstall ubuntu and as long as you make your ubuntu partition smaller and then reformat the new unallocated partition only you should be ok.

---

### Post by raymondh on 2010-01-15
> **freefixkorma said:**
> hi guys i am sorry if this is not the correct subject to post i have ubuntu 9.04 i want to know if i can do a partition base on what i have right now cause when i installed ubuntu i didnt do the partition to install windows so i want to do it now or in any case how can i reinstall ubuntu again without loosing my data store in my hard drive will appreciate any advise concerning this issue please post any help what is best to be perform in my pc i am very happy with ubuntu and wanna keep with it but sometimes a have some app in windows that i need thanks in advance

you can also use the livecd to access gparted as that will unmount the partitions for you which is required when doing partitioning work [here is a link regarding partitioning using gparted]("http://gparted.sourceforge.net/larry/resize/resizing.htm") after you get to ceate the windows partition you might want to format it to ntfs already so that you can easily identify it when you get to install windows and don't forget that after you install windows it will overwrite the mbr with it's own bootloader so you'll need to [re-install grub]("http://ubuntuforums.org/showthread.php?t=224351") once again in order to be able to dual-boot

:)
Raymond

PS: don't forget to have a working/tested back-up of your files before doing any partitioning work

---

### Post by audiomick on 2010-01-15
if you install windows after ubuntu, it will mess up your Grub. You will have to re-install grub.
9.04 uses grub legacy. there are instructions how to recover it after a windows install here.
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by freefixkorma on 2010-01-15
i try to use that app gparted it does not allow me to choose the hd i am following the instructions of the app and nothing i will do it with the live cd hope i have better luck there thanks for your help

---

### Post by freefixkorma on 2010-01-15
i try the gparted it does not allow me to resize the hd i am following the instructions and does not allow me to do it if u have any idea and how to will appreciate that

---

### Post by alwayshere on 2010-01-15
you could use virtualbox
 [http://www.virtualbox.org/]("http://www.virtualbox.org/")

to install it put below in terminal

sudo apt-get install virtualbox

---

### Post by Leppie on 2010-01-15
> **freefixkorma said:**
> i try the gparted it does not allow me to resize the hd i am following the instructions and does not allow me to do it if u have any idea and how to will appreciate that
you have to resize your ubuntu partition using the livecd or something similar. you cannot resize a mounted system (hence if you booted into your normal system, you won't be able to resize its partition)

---

### Post by freefixkorma on 2010-01-15
i will try to do it with the live cd cause i did not have luck with the gparted i download the app and when i try to resized the hd all the options where not available to perform sorry i am dummy with this issues i will do it with the live cd if there is any help and how to with live cd please place the link will appreciate that thanks

---

### Post by alwayshere on 2010-01-15
[https://help.ubuntu.com/community/LiveCD]("https://help.ubuntu.com/community/LiveCD")

---

### Post by Leppie on 2010-01-15
> **freefixkorma said:**
> i will try to do it with the live cd cause i did not have luck with the gparted i download the app and when i try to resized the hd all the options where not available to perform sorry i am dummy with this issues i will do it with the live cd if there is any help and how to with live cd please place the link will appreciate that thanks
especially have a look at the resizing partitions section: [https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)
bear in mind that if your system is using UUID (which i believe jaunty does), you will also have to edit your grub's menu.lst and fstab (and possibly other configuration files) to match the new UUID that will be created for the partition.

---

