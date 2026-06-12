---
title: "Best practice to setup my partitions on installation Kubuntu"
date: 2023-01-21
forum: Installation &amp; Upgrades
---

### Post by netw844f on 2023-01-21
Hello folks,

I intend install Kubuntu 22.04.1LTS on my:

Processors: i3-9100F CPU 3.60GHz
Memory: 16GiB of RAM
Graphics Processor: NVIDIA GeForce GT 710/PCIe/SSE2
WD_BLACK SN750 NVMe SSD - 500GB

but I would like choose the right installation type because I intend have an option to format my system in the future without wipe out all my data. I was searching for articles and videos where I can see how I should configure all partition and I found this video: [https://www.youtube.com/watch?v=Wc4GjV_Ahb8&t=345s](https://www.youtube.com/watch?v=Wc4GjV_Ahb8&t=345s)

He selected this setup partitions:

sda1 efi with 100mb
sda2 / I will choose 40GB - What do you think?
sda3 /home I am thinking choose 440GB - please see next point to understand why I mention this value
sda4 swap 20GB because on this article mention 20GB to the ram size 16GB if I want hibernation option - [https://itsfoss.com/swap-size/](https://itsfoss.com/swap-size/)

Is hibernation is the same sleep option?

I already have an installation of the Kubuntu on my computer, on another hard drive. Which cares I should take during the installation to disable/erase the option (modify the grub) from this hard drive/installation I use currently?

What do you think?
Thank you in advance for your help

---

### Post by yancek on 2023-01-21
I would suggest reading through the article at the link below to start.  It is quite old and I don't know if there have been any changes with the installer as I do not use Kubuntu.  Read through the arricle before beginning.  Select the option for a manual install to specify partitions.

The partition sizes you have selected should be fine.  There is no ideal or standard, it depends on the user wishes and size of drives available.  If you intend to keep the Kubuntu install, you should have that option available but if possible, you could disconnect the drive on which your current Kubuntu exists.

Is your current install of Kubuntu an EFI install?  If it is, the Kubuntu install may put the EFI files for the new Kubuntu on the EFI partition of the first install.

[https://help.ubuntu.com/community/GraphicalInstall/Kubuntu](https://help.ubuntu.com/community/GraphicalInstall/Kubuntu)

---

### Post by Impavidus on 2023-01-21
> **netw844f said:**
> 
Is hibernation is the same sleep option?

No. Sleep is also called suspend to RAM. It shuts down most parts of the computer, but keeps RAM active, so when you restart, you can immediately resume your work. The computer still uses a small amount of power, so a desktop can't be unplugged when in sleep mode and a laptop only for a few days. Hibernation is also called suspend to disk. It copies the contents of RAM to swap, then shuts down the entire computer. When you restart, it has to read all contents back from swap to RAM before you can resume your work, so it's slower than sleep, but the computer uses no power at all. Further, the contents of swap can be read (for example from a live disk) or even altered while the system hibernates, so there can be security implications. Hibernation is by default disabled on Ubuntu.

---

### Post by netw844f on 2023-01-24
> Is your current install of Kubuntu an EFI install? 

I think so. What I am waiting is the new installation Kubuntu will install alongside to the older installation. The process update the grub. I only need maintain old installation because I need copy all my data from this disk to other, where this last which will receive the new installation kubuntu.

---

### Post by netw844f on 2023-01-24
> No. Sleep is also called suspend to RAM. It shuts down most parts of the  computer, but keeps RAM active, so when you restart, you can  immediately resume your work. The computer still uses a small amount of  power, so a desktop can't be unplugged when in sleep mode and a laptop  only for a few days. Hibernation is also called suspend to disk. It  copies the contents of RAM to swap, then shuts down the entire computer.  When you restart, it has to read all contents back from swap to RAM  before you can resume your work, so it's slower than sleep, but the  computer uses no power at all. Further, the contents of swap can be read  (for example from a live disk) or even altered while the system  hibernates, so there can be security implications. Hibernation is by  default disabled on Ubuntu.

Thank you kindly from your great explanation about difference sleep and hibernation. Do you recommend any article or tutorial to following to learn how configure/enable option hibernation on Kubuntu?

---

### Post by Impavidus on 2023-01-24
This guide looks decent: [https://ubuntuhandbook.org/index.php/2021/08/enable-hibernate-ubuntu-21-10/](https://ubuntuhandbook.org/index.php/2021/08/enable-hibernate-ubuntu-21-10/)
I cannot guarantee it will work or is even safe to use.

Note that at some point it tells you to run sudo gedit. gedit may not be included on Kubuntu, but you can use a different text editor. In fact, running a GUI text editor with sudo has caused a lot of trouble, somewhat reduced since sudo uses the -h option by default now. The preferred way to edit root-owned files is to use sudoedit:```
sudoedit somefile
```That increases security by not running the editor as root, but only copying the result back as root.

Also note that I'm not fully confident that the proposed method to use hibernate with a swap file is fully reliable. I suggest you use a swap partition anyway.

---

