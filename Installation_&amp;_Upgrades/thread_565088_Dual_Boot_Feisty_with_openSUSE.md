---
title: "Dual Boot Feisty with openSUSE"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by vgrisham on 2007-10-01
Hello,

I have Ubuntu Feisty installed on an internal SATA hard drive. I also have openSUSE installed on a second internal hard drive (openSUSE works with my snapscan USB scanner; Feisty won't). For a while, I've just been switching the cables between the drives whenever I want to boot openSUSE. I'm sure however there is a more polished way to to this. 

Essentially what I would like is for Grub to pop up with Feisty as default and with SUSE as a secondary menu option. Both operating systems are installed on their drives' master boot records.

How would I go about creating this environment?

Thanks,
Vaughn

---

### Post by Pumalite on 2007-10-01
hoose which system you want to 'own' the grub, then post:
sudo fdisk -lu
cat /boot/brub/meu.lst

---

### Post by vgrisham on 2007-10-02
I want Ubuntu to control things. After these commands in Ubuntu, do I need to do anything in openSUSE?

---

### Post by Pumalite on 2007-10-02
Go to Ubuntu then and post the output of the commands.

---

### Post by vgrisham on 2007-10-02
Pumalite,

Thank you for your help, but I've just learned that the latest build of Gutsy solved the snapscan/usb conflict that I was experiencing and that was preventing my scanner from working. I no longer plan on dual booting.

Thanks!

---

### Post by Pumalite on 2007-10-02
You are welcome. I'm glad for you.

---

