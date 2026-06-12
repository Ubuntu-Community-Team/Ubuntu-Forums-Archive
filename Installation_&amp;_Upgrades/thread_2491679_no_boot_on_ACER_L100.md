---
title: "no boot on ACER L100"
date: 2023-10-17
forum: Installation &amp; Upgrades
---

### Post by ortollj on 2023-10-17
Hi

I would like to install Ubuntu 22.04 instead of W7 on an old Acer L100 PC, on a new hard drive that I have already formatted, I know after already installing Ubuntu that the boot does not take place, the Bios does not see Ubuntu , I have just finished the installation and I am in test mode. I haven't rebooted the machine yet. Is there anything I can do at this level to make this PC reboot on Ubuntu? (install Grub or something else?)
[IMG]https://docs.google.com/document/d/18y7kH74ihi91eCGkkVXtVfxHJ1pPyVFeB2k4x6HcMWQ/edit?usp=sharing[/IMG]

---

### Post by ajgreeny on 2023-10-17
I don't think you will ever get that old and very low spec notebook to run any supported versions of Ubuntu nor probably any of the alternative flavours off the *ubuntu family, eg Lubuntu or Xubuntu.

According to my search it has only 1G ram and a single core, or maybe dual core depending on the exact model, and that is not good enough to run most up to date Linux distros.

---

### Post by sudodus on 2023-10-17
You can probably run some current version of **Puppy Linux** or **Tiny Core** in that computer (but as ajgreeny already wrote, most up to date Linux distros need more CPU horsepower and more RAM (memory)).

Edit: If you have more than 1 GB RAM you *might* get Lubuntu or Xubuntu running (because I think it is a 64-bit processor).

---

### Post by Rubi1200 on 2023-10-17
If Xubuntu or Lubuntu won't work, then consider the following distros:

AntiX
Bodhi Linux

Bodhi is Ubuntu based but with the lightweight Moksha desktop environment.

I have successfully installed and tested both on an Acer 1GB netbook. Some things, like browsers or video, might run a bit slowly at times but other than that you have a fully functional Linux distro to play with.

---

### Post by ortollj on 2023-10-17
ok, but am I not going to fall into the same boot problem again? I will try installing Bhodi Linux later because these installation problems are very time consuming.
Thanks

---

### Post by ActionParsnip on 2023-10-17
1Gb RAM will run better in Lubuntu better. That or any other super light distribution. The maximum RAM is 2Gb so that upgrade will really help your experience

---

### Post by ortollj on 2023-10-17
Finally the PC reboots on Ubuntu 22.04. I had turned off the PC, then I turned it back on, thinking that I would encounter boot problems again, but no , it works now !, however it is true that it slows down a bit, but the PC can be used to surf the net! I have the impression that installing in 2 steps works by using the installation icon on the desktop the second time before rebooting. Just after the first installation, as I was in test mode, I tryed to install Grub on sda, but I got COW error so I do not think it is this which solve the boot pb.

---

### Post by oldfred on 2023-10-17
Your installer flash drive must have been sda.
The cow error is because you tried to install grub to the live installer.
Many systems promoter USB flash drive to first drive or sda on reboot. 

I have an old Toshiba, last really used with 12.04. It is BIOS only with 1.5GB of RAM and slow HDD. Even with 12.04 if I loaded more than one larger app and a smaller app, it would go to swap & have a second or two of blank screen.
Tried installing Ubuntu 20.04 and it would not install. Server installed and was able to had a lightweight gui.
New laptop broke & I had to send it in just before trip. So pulled out old laptop, but added BIOS boot stanza on HDD to boot full install of Kubuntu 22.04 on external SSD. That was functional if a bit slow compared to desktops with SSDs that I am now used to.

Or consider an external SSD, if you want to use that lightweight system.

---

