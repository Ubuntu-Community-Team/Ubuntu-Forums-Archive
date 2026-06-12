---
title: "problems with dual boot"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by daviddoji on 2012-08-15
I had 3 partitions in my SSD:
1 - Windows system (100 MB), this partition is made by windows7 when you install it
2 - Windows 7 partition
3 - Kubuntu partition made by gparted 

I installed via Ubuntu USBlive in his partition, but after restarting, the system automatically loads windows without giving me the choice to choose which OS I want to use. The grub loader, by defect during the installation, was loaded in the second HDD (it is not in the same SSD I have the OS´s, maybe this is the problem).

In windows, I can see how my SSD has the size I gave, I mean, without the Ubuntu partition.

If I enter via USBlive, I can see the Ubuntu partition, but I don´t know what to change to have the choice to choose the OS I want to use.

How can I solve this?

Thanks

---

### Post by Mark Phelps on 2012-08-15
You said you had a second HDD on which you installed Linux.  Change the BIOS boot order to put that drive first.

Then, when you boot into Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the default GRUB config file and you should see it detect Windows 7 in the process.

Then, when you reboot, you should see a GRUB menu.

---

### Post by daviddoji on 2012-08-15
No. I installed Kubuntu in the same SSD I have windows 7.
I installed the grub loader in the second HDD.

---

### Post by oldfred on 2012-08-15
As Mark Phelps said, you have to boot from the drive you installed the grub2 boot loader into. The MBR on the other drive will just load the install in the SSD.

You can change BIOS to permanent boot from that drive or test by using a one time boot key that most systems have. My system uses f12, but it varies by vendor.

---

