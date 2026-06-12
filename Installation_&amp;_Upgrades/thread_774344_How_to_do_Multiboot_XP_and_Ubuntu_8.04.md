---
title: "How to do Multiboot: XP and Ubuntu 8.04?"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by carlcx on 2008-04-29
How can I install Windows XP and Ubuntu 8.04 in my 80 GB hard disk?
What should I install first? 
How much partition would I allocate for Windows XP or Linux

---

### Post by bigken on 2008-04-29
like biggus says install windozs 1st I would give it about 20 gig 
then when you install ubuntu use the manual option to create 
your partitions personally I would do it this way 

10gig / (system)
10 gig /home 
the rest fat32 this will give you storage for windozs and ubuntu


how much ram do you have if you have less than 2gig make a linux swap partition two mtimes your ram ie 512mb = 1gig swap

---

### Post by Rallg on 2008-04-29
(1) Install Windows first. Reason: When you later install Ubuntu, its bootloader can recognize that Windows XP is already installed. But Windows will not recognize Ubuntu (or any Linux).

(2) What do you intend to do with Ubuntu? If you do not intend to work with many large files or multimedia, and are not trying to set up an elaborate compiling and development environment, 5Gb is more than enough room. A few more Gb might be helpful. You will also need some room for the "Linux Swap" partition. Twice the size of your RAM is generally recommended for swap, but you can get by with much less than that, if you have a large RAM and don't want to use too much hard drive for swap (I believe the minimum is 256M swap).

(3) Consider creating a spare partition, formatted to FAT32. This can be a common area, accessible via either Windows or Linux. The amount of space should be large enough to accomodate any files that you think you might want to access via either system. (Note, I am not referring to Windows programs accessed via WINE.)

(4) Before installing Ubuntu (or any Linux), be sure to read through various how-to guides to ensure that you choose the correct installation options. If you simply accept all defaults during the installation process, you may find that Linux takes up more space than you intended to give it.

(5) Before installing any Linux, try it on live CD. That will (usually) expose any hardware incompatibilities for your computer. Also, keep in mind that certain hardware drivers cannot be shipped with the Linux installer, because they are proprietary. If you have that hardware, you will have to acquire the extra drivers via (cable) Internet.

---

### Post by uidb4056 on 2008-04-29
You have to install XP first, even if you have allocated all the disk to XP with 8.04 you can take advantage of Wubi istaller that comes with Ubuntu Live CD, this let you to have a test Ubuntu system without having to install GRUB in MBR, it simulates a file system using free space in your NTFS file system and adds a boot option in yor windows boot giving you a dual boot system.

There is a wizard when rou run Wubi that asks you where want ubuntu located, your user name and password and begins the install. Ubuntu is installed automatically and you have a dual boot system without having to deal with partitions, the performance is a little bit lower but if you have good specs you don't notice it.

If you later on wants to remove Wubi you can do on XP from add/remove programns and the wizard asks you if you want to backup your ubuntu for later reuse.

---

### Post by carlcx on 2008-04-30
hey, thanks for the help! Yes, I've installed Windows XP Home Edition and Ubuntu well! It's great!

---

