---
title: "ubuntu over Kali installation"
date: 2017-05-04
forum: Installation &amp; Upgrades
---

### Post by vetabz on 2017-05-04
Hi,

I have a KALI+Windows8 on a 64bit hardware. Now I wanted to install Ubuntu over KALI and I dont want to messup and endup fixing things so I turn to you guys. Is there a step by step guide that I can follow on how to do this from start to finish.

My KALI partition is 35Gb is it possible to expand it a bit during installation.

---

### Post by yancek on 2017-05-04
First, determine if your windows is using UEFI/GPT.  If it was pre-installed, it almost sure is.  Then take a look at the Ubuntu documentation page on dual booting with windows at the link below. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You would need to post more information on the layout of your drives/partitions before anyone could definitively tell you if you can increase the size of the old Kali partition without causing problems.  Using a terminal, get the output of the command:  gdisk -l (Lower Case Letter L in the command) or post an image of the GParted windows for your drive.  GParted is on the Ubuntu install DVD.

---

### Post by vetabz on 2017-05-04
Below are screenshots of the BIOS mode and the partitions of my disk.

I also looked this up in setupact.log in windows:
IBS    Callback_BootEnvironmentDetect: Detected boot environment: EFI

[https://1drv.ms/f/s!An-2FkNEf97mglZamQlL8_HT5sIu](https://1drv.ms/f/s!An-2FkNEf97mglZamQlL8_HT5sIu)

Kindly go to the link instead I can't post the images, maybe because I only got short URLs

[IMG]https://1drv.ms/i/s!An-2FkNEf97mglfyqy5FJk7ZRtyP[/IMG]

[IMG]https://1drv.ms/i/s!An-2FkNEf97mglfyqy5FJk7ZRtyP[/IMG]

---

### Post by oldfred on 2017-05-04
Be sure to boot installer in UEFI mode as that controls whether you install in UEFI or BIOS boot mode.
You can also tell mode installer is booted by screen shots in link in yancek's post above.

Use Something else install option and choose (change button) the existing ext4 partition as new / (root) partition. It will auto find swap and then you should be able to install. For location of grub boot loader be sure to select drive like sda. But with UEFI it always installs to sda, currently.

---

### Post by vetabz on 2017-05-06
Thank you all, I'm now running Ubuntu+Win8.1!!!

---

