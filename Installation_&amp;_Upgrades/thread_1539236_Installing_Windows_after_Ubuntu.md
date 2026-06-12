---
title: "Installing Windows after Ubuntu"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by tcchris on 2010-07-26
Sorry if this is obvious .
I have a Lucid install on my system , and I would like to install Windows XP on a separate hard drive . I am trying to get the A+ Cert , maybe change careers due to economy . That's another story .
I don't have a problem reinstalling Ubuntu after I get XP going if necessary , but I would like an easier method if possible .
I thought there might be an easier method since I have two hard drives .
Also , does any one know if windows asks which hard drive ? I would hate for it to overwrite my home directory

---

### Post by VH-BIL on 2010-07-26
Most bois today have an option to choose which hard drive you would like to boot from. This is how I load windows (Just for playing blu rays). I unplug all hard drives except the one I am installing windows and install windows. when you plug it all together you can press the bios boot menu button then load windows by selecting the right drive.

---

### Post by uidb4056 on 2010-07-26
If you don't need gaming, or access specific hardware you can evaluate to install Win XP on a virtual machine VirtualBox, this way you don't need to restart to go from Ubuntu to XP or XP to Ubuntu. However this means you have minimum memory and CPU on your system to run virtual machines.

Link to VirtualBox [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by tcchris on 2010-07-26
That is a great idea , I did not think of unplugging the drive .

---

### Post by tcchris on 2010-07-26
I really want a separate install . I probably won't use it much , but I'd like it separate anyway . Will grub load the separate OS's if I update grub later ?

---

### Post by VH-BIL on 2010-07-26
yes it will. If you decide to install windows with your Linux drive connected, Windows will overwrite your MBR.

---

### Post by tcchris on 2010-07-26
Great help guys 
unplug ubuntu drive
install windows
plug in ubuntu drive
boot ubuntu
update grub

Very good , thanks

---

### Post by VH-BIL on 2010-07-26
Unpluging the Ubuntu drive was mainly if you had and wanted to use the bios boot menu, but I am glad it worked...

---

