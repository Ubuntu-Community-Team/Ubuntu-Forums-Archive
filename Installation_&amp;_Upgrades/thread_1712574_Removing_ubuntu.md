---
title: "Removing ubuntu"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by donpeter06 on 2011-03-22
I have installed 2 copies of ubuntu 10.10 in 2 partitions in the same HDD.
I would like to remove the old copy which has a resolution problem without compromising the new copy.
Also my Grub has both copies shown at the boot time.
As i dont know where the Grub is located(new or old). If i format the old partition i might loose the grub and hence the installation could be a problem.
Please Help.

---

### Post by Hedgehog1 on 2011-03-22
> **donpeter06 said:**
> I have installed 2 copies of ubuntu 10.10 in 2 partitions in the same HDD.
I would like to remove the old copy which has a resolution problem without compromising the new copy.
Also my Grub has both copies shown at the boot time.
As i dont know where the Grub is located(new or old). If i format the old partition i might loose the grub and hence the installation could be a problem.
Please Help.
 
donpeter06,
 
Please boot up in the Ubuntu you want to keep.
 
From the terminal do:
```
sudo [COLOR=black]grub-install[/COLOR]
```
This makes sure grub is installed from your active version of Ubuntu
 
Next, run gparted or the disk utility and delete or reformat the unwanted Ubuntu partition.
 
From the terminal do:
```
sudo update-grub
```
This removes the now formatted/deleted version of Ubuntu from the grub menu.
 
The Hedge
 
:KS

---

### Post by tommcd on 2011-03-22
If you installed the second (i.e., the one you wish to keep) 10.10 last, then it is likely that it controls the MBR. As long as you have not performed an update to the first (i.e., the one you want to get rid of) 10.10 that included a kernel update, then the first 10.10 more than likely no longer controls the MBR.
So just reformat the first 10.10 partition. Worst case scenario is that you will need to reinstall grub2 to the MBR from the Ubuntu install CD. See this for more info: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

