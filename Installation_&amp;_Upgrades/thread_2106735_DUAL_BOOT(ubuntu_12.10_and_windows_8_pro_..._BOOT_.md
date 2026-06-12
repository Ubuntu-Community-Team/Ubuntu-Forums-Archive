---
title: "DUAL BOOT(ubuntu 12.10 and windows 8 pro ... BOOT LOADER PROBLEM..."
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by visitnag on 2013-01-19
Hi,

I have first installed windows7 ultimate and later UBUNTU 12.10. Later I have upgraded my win-7 with windows 8 pro.
 Now my problem is I am unable to access UBUNTU as my boot loader is missing. Kindly help me to recover the boot loader.

Help is appreciated.

Thank you in adavance

---

### Post by Bucky Ball on 2013-01-19
*Thread moved to** Installations & Upgrades***

---

### Post by leclerc65 on 2013-01-19
a- boot with an Ubuntu live CD, option 'Try Ubuntu'
b- Open a terminal then do
sudo mount /dev/sdaX /mnt 
(replace X with the number of the partition where Ubuntu is installed, also assuming your hard drive is SDA) 
sudo grub-install --root-directory=/mnt/ /dev/sda
c- reboot, you should have Ubuntu by now
sudo update-grub
reboot , you should see options to boot Ubuntu & Windows

---

### Post by visitnag on 2013-01-19
Hi,

I have first installed windows7 ultimate and later UBUNTU 12.10. Later I have upgraded my** win-7 with windows 8 pro.**
Now my problem is I am unable to access **UBUNTU as my boot loader is missing**. Kindly help me to recover the boot loader.

Help is appreciated.

Thank you in adavance

---

### Post by visitnag on 2013-01-19
How do I know on which partition my ubuntu is loaded? Mine is 1TB harddisk.

---

### Post by visitnag on 2013-01-20
[SIZE="2"]Help me please...... or Do I have to reinstall UBUNTU?[/SIZE]

---

### Post by baldawat on 2013-01-20
May be u remember that at the time of Ubuntu installation how many ext partitions you have created.
 
Just mount each /dev/sda[COLOR=red]**X  **[COLOR=black]one by one[/COLOR][/COLOR][COLOR=black]by creating few temporary folders, try to read the content of these folder you get know know on which partions you installed /root, /home, swap etc. [/COLOR]
 
**[COLOR=red]X[/COLOR]** - represent partion number.;)

---

### Post by Old_Grey_Wolf on 2013-01-20
Try using boot-repair [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2013-01-20
If you want a gui to do it automatically, you can install this to your Ubuntu Live installer or download a full repair ISO.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by howefield on 2013-01-20
Threads merged.

---

### Post by greg_ory on 2013-01-20
Is there any particular reason why you do not want to use Ubuntu only?

---

### Post by leclerc65 on 2013-01-21
> **visitnag said:**
> How do I know on which partition my ubuntu is loaded? Mine is 1TB harddisk.
sudo fdisk -l

---

