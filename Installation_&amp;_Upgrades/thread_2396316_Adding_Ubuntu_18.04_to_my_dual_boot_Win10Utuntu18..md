---
title: "Adding Ubuntu 18.04 to my dual boot Win10/Utuntu18.04 no space too etc."
date: 2018-07-13
forum: Installation &amp; Upgrades
---

### Post by chris walters on 2018-07-13
I must keep Win10 working. I am currently using Win10 and grub as my boot loader. I have a working Ubuntu 18.04 system with very limited space. I want to put Ubuntu on my 1.5TB drive and keep Win10 booting OK. I don't know where Grub is or where I should tell the Installer grub is. How can I find out? Win10 is on another drive, size 500GB letter "C:".
I am a very experienced microcomputer programmer, around 47 years of computer experience. But very little Unix/Linux knowledge. I am also looking for a Ubuntu friend. Thank you all for any help. On a quad core AMD 65 bit.
Sincerely,
Chris Walters
PS I don't even know how to edit grub.

---

### Post by oldfred on 2018-07-13
This shows lots of details in one report.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by westie457 on 2018-07-13
Hello chris walters. We are all quite friendly here at UF.

To give us a clue of what your situation regarding your current installation and what you want to achieve we are going to need some more information.
The easiest way for you to supply most of this for you to follow requests and instructions.
Please go to here, [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair), scroll to the 2nd option to install Boot Repair.
When the app is running could you click on the 'Create Bootinfo summary' button and post the generated link here.
Once we have that we can offer further advice about Grub and partitions.

Now a small bit of education; Windows uses 'drive and letter' which in effect is a partition. Linux uses '/dev/sda1' for example. Where sda is the first hard drive - sdc would be the third hard drive. The number is for a partition (1 - 4) with an MBR partition-table, which is the limit unless you have something called an 'extended partition' which is a container to allow the creation of many more 'logical' partitions inside the container.
The newer GPT partition-table only uses 'Primary' partitions, upto 128 partitions per hard drive.

I also have no real clue on how to edit Grub, I usually search the forums for most things and follow directions.

---

