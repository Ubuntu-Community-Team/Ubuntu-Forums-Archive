---
title: "Cannot Boot Ubuntu 8.04 install on an external Hard drive"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by samknex on 2008-05-08
I have been frustrated with this for a few days now, and I need help. I have a Sony, P4 2.4ghz, 512mb ram, and a 80gb internal hard drive, a 200gb internal hard drive, and a 500gb **external** hard drive.

Now, what I am trying to do is to install Ubuntu 8.04 on the external hard drive and keep my windows install on the 80gb internal hard drive. Now here is the twist. I also have another install of Windows that is Non-functioning and just appears when I boot up the computer. I have been able to successfully install Ubuntu on the external hard drive, but when I try to boot from it ( I am assuming that I just select it just like you select the windows partitions) it doesn't show up. 

that is really all the information that I can or know how to give, being relatively new to Ubuntu. any help would be appreciated. And if you need any further info, just ask me.:confused:

---

### Post by Pumalite on 2008-05-08
Post:
sudo fdisk -l
cat /boot/grub/menu.lst (from your external drive)

---

### Post by samknex on 2008-05-08
> **Pumalite said:**
> Post:
sudo fdisk -l
cat /boot/grub/menu.lst (from your external drive)
where should I enter that? I am a serious noob.

---

### Post by G_wiz on 2008-05-09
enter it into the Terminal.
To open, click Applications, then highlight Accessories, then click on Terminal

---

### Post by Pumalite on 2008-05-09
Boot your Live CD if you have to. (to get to a Terminal)

---

