---
title: "I'm planning to set up triple boot XP/Backtrack/Ubuntu11.10"
date: 2012-03-19
forum: Installation &amp; Upgrades
---

### Post by fjanos on 2012-03-19
[SIZE=2]I'd like to have a triple boot system XP/BACKtrack/Ubuntu11.10
What are the steps do I have to take?
I already have XP and Ubunut 11.10 installed. How can I attach Backtrack 5 and to boot Ubuntu as default? [/SIZE]

---

### Post by grahammechanical on 2012-03-19
You will first need to create a partition or partitions for Backtrack.

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

You need to find out how to install Backtrack from the Backtrack web site. You install it in the partition that you have created for it.

Backtrack may put its own bootloader in the hard disk MBR (Master Boot Record). So, you have to load Ubuntu 11.10 and run the command in a terminal

```
sudo update-grub
```

That will put the Ubuntu 11.10 Grub boot loader back in charge with Ubuntu 11.10 as the default.

You should first of all think about installing a utility called Grub Customizer in 11.10

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

That will let you edit the Grub menu and it will help to keep 11.10 as the default OS in the menu list. Grub Customizer will run the update-grub for you when you click Save or Save to MBR.

Regards.

---

### Post by fjanos on 2012-03-20
First of all thank you for the first answer. Ok, let's suppose I create a partition and install Backtrack on that partition. After restart my computer will I get a Grub Boot Menu with a menu list: XP/Ubuntu/Backtrack? Or I have to customize something.

---

### Post by oldfred on 2012-03-20
Not sure what boot loader backtrack uses, grub legacy or grub2. Either way it is best just to install grub to the Backtrack partition and never use it. The the update grub in Ubuntu will find the Backtrack install. Ubuntu does not offer the choice to not install a grub boot loader, so installing to the partition is just a work around.

Otherwise you have to reinstall the Ubuntu grub2 boot loader to the MBR. And if Backtrack lets you boot Ubuntu that can be done easily from inside Ubuntu or else you have to use liveCD or Backtrack to mount Ubuntu partition and install Ubuntu's grub2 to MBR.

Either way best to have Ubuntu liveCD of the same version you have installed. If upgraded download the current version. Grub 1.99 needs to be reinstalled from the same version.

---

