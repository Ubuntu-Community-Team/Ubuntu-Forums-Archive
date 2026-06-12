---
title: "dual boot ubuntu 10.10 and 11.10"
date: 2012-03-08
forum: Installation &amp; Upgrades
---

### Post by tazman550 on 2012-03-08
Hello 

  I would like to dual boot 10.10 and 11.10 they are both installed and on separate

     drives , how would I go about doing this ??

---

### Post by oldfred on 2012-03-08
Welcome to the forums.

Have you installed or do you want to install?

You can disconnect drive which absolutely insures each is separate. Otherwise you have to use manual install (Something Else) to have the option where to install the grub2 boot loader.

Do you want to share any data? I prefer to have a separate data partition which I can mount in both installs to share data without issue.

---

### Post by tazman550 on 2012-03-08
yes I have 10.10 on one drive and I installed 11.10 on a separate drive to see if I wanted to keep it or not .  basically wanting to pick which drive to boot on system start ..    sorry kind of new to Ubuntu

---

### Post by pavi_elex on 2012-03-09
Does it not ask you before booting to picking up your desired OS?

---

### Post by oldfred on 2012-03-09
Grub2 usually auto installs to sda. Did you specify otherwise? I prefer to have each grub2 boot loader in the same MBR as the Ubuntu install.

You can boot into either Ubuntu and run 
sudo update-grub

You should be able in BIOS to select which drive to boot from but if your second install put grub into sda then sdb may not be bootable.

You can reinstall grub easily if you can boot into each system.

Grub also remembers which drive to reinstall to:
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by tazman550 on 2012-03-09
Thank you very much OldFred the sudo update-grub worked perfect

---

