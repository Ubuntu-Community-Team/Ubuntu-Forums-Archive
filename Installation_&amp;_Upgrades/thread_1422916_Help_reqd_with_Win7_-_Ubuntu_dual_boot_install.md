---
title: "Help reqd with Win7 - Ubuntu dual boot install"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by prasha on 2010-03-05
[FONT="Arial"]Hello All,
I currently have Win 7 HP installed on my HP dv4 laptop with T6600 processor, 300GB HDD & 4GB RAM. My objective is to install ubuntu 9.10 with Windows 7 in the dual-boot mode. I am writing down the steps I suppose I have to follow. Please correct/advise me wherever you feel I have gone wrong or could go better. 


1. Create a separate partition for Ubuntu (install and usage) by shrinking my C drive.
2. Create another partition double the size of my RAM for using it as swap.
3. Restart the machine with the Live CD inserted and select 'Try ubuntu without any change to your computer' to see if things are running fine with the CD.
4. After the Booting is done, click on Install.
5. Fill in sequentially the language, Timezone and keyboard layout.
6. After reaching the prepare disk space screen, choose 'Specify Partitions manually'.
7.On the prepare partition screen, I will be able to figure out the partition for Ubuntu and Swap with their size.
8.Select the partition created for Ubuntu configure it as 'ext4' with mount point '/', also click format partition.
9.Select the partition created for Swap, and configure it as 'linux swap'.
10. Clicking on forward should take me to the screen which asks to fill name and password details.
11. Clicking on forward and install should start the installation process.

Thanks in advance :)[/FONT]

---

### Post by zvacet on 2010-03-08
Everything look good but I will make two suggestions:

1. you don't need 8GB for swap because you have enough ram.Give 2GB to swap.

2.I will make another partition for home.That way you will be able to do fresh install,upgrades... without losing your data/settings.

On free space you want to dedicate to Ubuntu I will give 10GB for root,2GB for swap and rest for home.Home will be ext4 mountpoint /home.

---

### Post by oldfred on 2010-03-08
Use windows tools to shrink windows and reboot it several times to make sure it is ok with the resize.

If you use gparted without unchecking the checkbox it moves the start of windows from sector 2048 to sector 63 as XP & linux use sector 63. This causes windows problems and requires windows boot repairs.

---

